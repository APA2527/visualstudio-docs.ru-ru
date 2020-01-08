---
title: Установка Visual Studio Build Tools в контейнер
titleSuffix: ''
description: Узнайте, как установить средства Visual Studio Build Tools в контейнере Windows для поддержки процессов непрерывной интеграции и поставки.
ms.date: 07/03/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: cdec0c6059775f4542e7b012709e20ad45c249cc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595973"
---
# <a name="install-build-tools-into-a-container"></a>Установка Build Tools в контейнер

Средства Visual Studio Build Tools можно установить в контейнере Windows для поддержки процессов непрерывной интеграции и поставки. В этой статье описываются необходимые изменения конфигурации Docker, а также [рабочие нагрузки и компоненты](workload-component-id-vs-build-tools.md), которые можно установить в контейнере.

[Контейнеры](https://www.docker.com/what-container) — это отличное средство для упаковки согласованной системы сборки, которую можно использовать не только в серверной среде непрерывной интеграции и поставки, но и в средах разработки. Например, вы можете поместить исходный код в контейнер, сборка которого будет выполняться в настраиваемой среде, и в то же время продолжать использовать Visual Studio или другие средства для написания кода. Если в рамках рабочего процесса непрерывной интеграции и поставки используется тот же образ контейнера, можно быть уверенным в том, что сборка кода будет производиться согласованно. Контейнеры можно также применять для обеспечения согласованности среды выполнения. Это обычный сценарий для микрослужб, использующих несколько контейнеров с системой оркестрации, однако он выходит за рамки этой статьи.

Если возможностей средств Visual Studio Build Tools недостаточно для сборки исходного кода, эти же инструкции можно использовать для других продуктов Visual Studio. Однако имейте в виду, что контейнеры Windows не поддерживают интерактивный пользовательский интерфейс, поэтому все команды должны быть автоматизированы.

## <a name="before-you-begin"></a>Подготовка к работе

Ниже предполагается, что вы знакомы с некоторыми функциями [Docker](https://www.docker.com/what-docker). Если вы еще знаете, как работать с Docker в Windows, прочитайте статью об [установке и настройке модуля Docker в Windows](/virtualization/windowscontainers/manage-docker/configure-docker-daemon).

Используемый далее базовый образ является примером и может не подойти для вашей системы. Ознакомьтесь со статьей [Windows container version compatibility](/virtualization/windowscontainers/deploy-containers/version-compatibility) (Совместимость версий контейнеров Windows), чтобы определить, какой базовый образ вам следует использовать для среды.

## <a name="create-and-build-the-dockerfile"></a>Создание и сборка Dockerfile

Сохраните приведенный ниже пример Dockerfile в новый файл на диске. Если файл имеет имя Dockerfile, он распознается по умолчанию.

> [!WARNING]
> В этом примере файла Dockerfile исключены только более ранние пакеты Windows SDK, которые невозможно установить в контейнерах. Более ранние выпуски приводят к сбою команды сборки.

1. Откройте окно командной строки.

1. Создайте каталог (рекомендуется):

   ```shell
   mkdir C:\BuildTools
   ```

1. Перейдите в этот каталог:

   ```shell
   cd C:\BuildTools
   ```

1. Сохраните в каталоге C:\BuildTools\Dockerfile представленное ниже содержимое.
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.2.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!WARNING]
   > Если образ основан непосредственно на microsoft/windowsservercore или mcr.microsoft.com/windows/servercore (см. статью блога о [переходе Майкрософт на модель объединения каталогов контейнеров](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)), платформа .NET Framework может не установиться правильно, причем сообщения об ошибках выводиться не будут. После завершения установки управляемый код может не запускаться. Вместо этого создайте образ на основе [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) или более поздней версии. Также обратите внимание, что образы, для которых указана версия 4.7.2 или более поздняя, могут использовать PowerShell в качестве `SHELL` по умолчанию, что будет приводить к сбою инструкций `RUN` и `ENTRYPOINT`.
   >
   > Visual Studio 2017 версии 15.8 или более ранней (любого продукта) не будет правильно установлена на образ mcr.microsoft.com/windows/servercore:1809 или более поздней версии. При этом сообщение об ошибке не отображается.
   >
   > Список версий ОС контейнеров, поддерживаемых определенными версиями ОС узлов, см. в статье [Windows container version compatibility](/virtualization/windowscontainers/deploy-containers/version-compatibility). Сведения об известных проблемах с контейнерами [см. в этой статье](build-tools-container-issues.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.8.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!WARNING]
   > Если образ основан непосредственно на microsoft/windowsservercore, платформа .NET Framework может не установиться правильно, причем сообщения об ошибках выводиться не будут. После завершения установки управляемый код может не запускаться. Вместо этого создайте образ на основе [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) или более поздней версии. Также обратите внимание, что образы, для которых указана версия 4.8 или более поздняя, могут использовать PowerShell в качестве `SHELL` по умолчанию, что будет приводить к сбою инструкций `RUN` и `ENTRYPOINT`.
   >
   > Список версий ОС контейнеров, поддерживаемых определенными версиями ОС узлов, см. в статье [Windows container version compatibility](/virtualization/windowscontainers/deploy-containers/version-compatibility). Сведения об известных проблемах с контейнерами [см. в этой статье](build-tools-container-issues.md).

   ::: moniker-end
   
   > [!NOTE]
   > Код ошибки `3010` указывает на успешное выполнение, после которого требуется перезагрузка. Дополнительные сведения см. в разделе [Сообщения об ошибках MsiExec.exe](/windows/win32/msi/error-codes).

1. Выполните в этом каталоге приведенную ниже команду.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Эта команда выполняет сборку файла Dockerfile в текущем каталоге, используя 2 ГБ памяти. Размер памяти по умолчанию, равный 1 ГБ, недостаточен, если установлены некоторые рабочие нагрузки. Однако в зависимости от требований вам, возможно, удастся выполнить сборку, используя всего 1 ГБ памяти.

   Итоговый образ помечается как "buildtools2017:latest", так что вы можете легко запустить его в контейнере как "buildtools2017", так как "latest" — это тег по умолчанию, используемый, если тег не указан. Если вы хотите использовать определенную версию средств Visual Studio Build Tools 2017 в более [сложном сценарии](advanced-build-tools-container.md), вы можете пометить контейнер конкретным номером сборки Visual Studio, а также тегом "latest", чтобы контейнеры применяли одну и ту же версию.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   Эта команда выполняет сборку файла Dockerfile в текущем каталоге, используя 2 ГБ памяти. Размер памяти по умолчанию, равный 1 ГБ, недостаточен, если установлены некоторые рабочие нагрузки. Однако в зависимости от требований вам, возможно, удастся выполнить сборку, используя всего 1 ГБ памяти.

   Итоговый образ помечается как "buildtools2019:latest", так что вы можете легко запустить его в контейнере как "buildtools2019", так как "latest" — это тег по умолчанию, используемый, если тег не указан. Если вы хотите использовать определенную версию средств Visual Studio Build Tools 2019 в более [сложном сценарии](advanced-build-tools-container.md), вы можете пометить контейнер конкретным номером сборки Visual Studio, а также тегом "latest", чтобы контейнеры применяли одну и ту же версию.

   ::: moniker-end

## <a name="using-the-built-image"></a>Использование собранного образа

После создания образа его можно запустить в контейнере для выполнения как интерактивной, так и автоматической сборки. В этом примере используется Командная строка разработчика, поэтому PATH и другие переменные среды уже настроены.

1. Откройте окно командной строки.

1. Запустите контейнер, чтобы запустить среду PowerShell, в которой заданы все переменные среды разработчика:

   ::: moniker range="vs-2017"

   ```shell
   docker run -it buildtools2017
   ```

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker run -it buildtools2019
   ```

   ::: moniker-end

Чтобы использовать этот образ для рабочего процесса CI/CD, его можно опубликовать в собственном [Реестре контейнеров Azure](https://azure.microsoft.com/services/container-registry) или другом внутреннем [реестре Docker](https://docs.docker.com/registry/deploying), откуда его могут извлекать серверы.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Расширенный пример для контейнеров](advanced-build-tools-container.md)
* [Известные проблемы для контейнеров](build-tools-container-issues.md)
* [Идентификаторы рабочих нагрузок и компонентов для Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
