---
title: Использование средств Visual Studio для Docker с ASP.NET Core
author: ghogen
description: Сведения об использовании средств Visual Studio 2019 и Docker для Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 124f60a4a632115625524b4e30ab28f795d41660
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2019
ms.locfileid: "71126121"
---
В Visual Studio можно легко выполнять сборку, отлаживать и запускать контейнерные приложения ASP.NET Core и публиковать их в Реестре контейнеров Azure (ACR), Docker Hub, Службе приложений Azure или собственном реестре контейнеров. В этой статье мы опубликуем приложение в ACR.

## <a name="prerequisites"></a>Предварительные требования

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) с рабочей нагрузкой **Веб-разработка**, **Средства Azure** и (или) **Кроссплатформенная разработка .NET Core**.
* [Средства разработки .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) для разработки с использованием .NET Core 2.2.
* Для публикации в Реестр контейнеров Azure требуется подписка Azure. [Зарегистрируйтесь для получения бесплатной пробной версии](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="installation-and-setup"></a>Установка и настройка

Чтобы установить Docker, сначала ознакомьтесь с разделом [Docker для Windows: что следует знать перед установкой](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Затем установите [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Добавление проекта в контейнер Docker

1. Создайте проект, используя шаблон **Веб-приложение ASP.NET Core**.
1. Выберите **Веб-приложение** и установите флажок **Включение поддержки Docker**.

   ![Флажок "Включение поддержки Docker"](../../media/container-tools/vs-2019/create-new-web-application.PNG)

1. Выберите нужный тип контейнера (Windows или Linux) и нажмите кнопку **Создать**.

## <a name="dockerfile-overview"></a>Общие сведения о Dockerfile

*Dockerfile* с инструкциями по созданию окончательного образа Docker создается в проекте. См. [справочник по Dockerfile](https://docs.docker.com/engine/reference/builder/) для получения сведений о других доступных в нем командах.

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["HelloDockerTools/HelloDockerTools.csproj", "HelloDockerTools/"]
RUN dotnet restore "HelloDockerTools/HelloDockerTools.csproj"
COPY . .
WORKDIR "/src/HelloDockerTools"
RUN dotnet build "HelloDockerTools.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "HelloDockerTools.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

Предыдущий *Dockerfile* основан на образе [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) и включает в себя инструкции по изменению базового образа путем сборки проекта и добавления его в контейнер.

Если в диалоговом окне создания проекта установлен флажок **Configure for HTTP** (Настроить для трафика HTTPS), *Dockerfile* предоставляет два порта. Один порт используется для трафика HTTP, другой — для HTTPS. Если флажок не установлен, для трафика HTTP предоставляется один порт (80).

## <a name="debug"></a>Отладка

Выберите пункт **Docker** в раскрывающемся списке отладки на панели инструментов, чтобы начать отладку приложения. Может появиться сообщение с запросом о доверии сертификату. Выберите доверие сертификату, чтобы продолжить.

В параметре **Инструменты контейнера** в окне **Вывод** показано, какие действия выполняются.

Откройте **консоль диспетчера пакетов** в меню **Сервис** > Диспетчер пакетов NuGet, **Консоль диспетчера пакетов**.

Итоговый образ Docker приложения помечается как *dev*. Образ основан на теге *2.2-aspnetcore-runtime* базового образа *microsoft/dotnet*. Выполните команду `docker images` в окне **Консоль диспетчера пакетов** (PMC). На компьютере отобразятся следующие образы:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> Образ **разработки** не содержит двоичные файлы приложения и другое содержимое, так как конфигурации **отладки** используют подключение томов для обеспечения итеративного редактирования и отладки. Чтобы создать рабочий образ со всем содержимым, используйте конфигурацию **выпуска**.

Выполните команду `docker ps` в PMC. Обратите внимание, что приложение выполняется с помощью контейнера:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        hellodockertools:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
```

## <a name="publish-docker-images"></a>Публикация образов Docker

После завершения цикла разработки и отладки приложения можно создать рабочий образ приложения.

1. Выберите в раскрывающемся списке конфигурации значение **Выпуск** и выполните сборку приложения.
1. В **обозревателе решений** щелкните правой кнопкой проект и выберите **Опубликовать**.
1. В диалоговом окне целевой публикации выберите вкладку **Реестр контейнеров**.
1. Выберите **Создать реестр контейнеров Azure** и щелкните **Опубликовать**.
1. Заполните нужные значения в окне **Создать новый реестр контейнеров Azure**.

    | Параметр      | Рекомендуемое значение  | ОПИСАНИЕ                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS-префикс** | Глобально уникальное имя | Имя, которое однозначно идентифицирует реестр контейнеров. |
    | **Подписка** | Выберите свою подписку | Подписка Azure, которую нужно использовать. |
    | **[Группа ресурсов](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Имя группы ресурсов, в которой создается реестр контейнеров. Чтобы создать группу ресурсов, выберите **Создать**.|
    | **[SKU](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | Стандартный | Уровень обслуживания в реестре контейнеров  |
    | **Расположение реестра** | Расположение рядом с вами | Выберите расположение в ближайшем [регионе](https://azure.microsoft.com/regions/) или в регионе, расположенном рядом с другими службами, которые будут использовать реестр контейнеров. |

    ![Диалоговое окно "Создание реестра контейнеров Azure" Visual Studio][0]

1. Нажмите кнопку **Создать**.

   ![Снимок экрана с сообщением об успешной публикации](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Следующие шаги

Теперь можно извлечь контейнер из реестра в любой узел, поддерживающий работу образов Docker, например [Экземпляры контейнеров Azure](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
