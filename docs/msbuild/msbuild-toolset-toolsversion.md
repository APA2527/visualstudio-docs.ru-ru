---
title: Набор инструментов MSBuild (ToolsVersion) | Документация Майкрософт
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4af4816440c2eb285a0f30db50e18108ce79265f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593812"
---
# <a name="msbuild-toolset-toolsversion"></a>Набор инструментов MSBuild (ToolsVersion)

В платформе MSBuild используется набор задач, целей и инструментов для построения приложения. Обычно в набор инструментов MSBuild входит файл *microsoft.common.tasks*, файл *microsoft.common.targets* и такие компиляторы, как *csc.exe* и *vbc.exe*. Большинство наборов инструментов позволяют компилировать приложения сразу для нескольких версий платформы .NET Framework и различных системных платформ. При этом набор инструментов MSBuild 2.0 можно использовать только для платформы .NET Framework 2.0.

## <a name="toolsversion-attribute"></a>Атрибут ToolsVersion
::: moniker range=">=vs-2019"
 Укажите набор инструментов в атрибуте `ToolsVersion` элемента [Проект](../msbuild/project-element-msbuild.md) в файле проекта. В приведенном ниже примере показано, что сборка проекта должна быть выполнена с помощью набора инструментов MSBuild 15.0 "Текущий".

```xml
<Project ToolsVersion="Current" ... </Project>
```

::: moniker-end

::: moniker range="vs-2017"
 Укажите набор инструментов в атрибуте `ToolsVersion` элемента [Проект](../msbuild/project-element-msbuild.md) в файле проекта. В приведенном ниже примере показано, что сборка проекта должна быть выполнена с помощью набора инструментов MSBuild 15.0.

```xml
<Project ToolsVersion="15.0" ... </Project>
```

::: moniker-end

> [!NOTE]
> Некоторые типы проектов используют атрибут `sdk` вместо `ToolsVersion`. Дополнительные сведения см. в разделах [Пакеты, метапакеты и платформы](/dotnet/core/packages) и [Дополнения к формату CSPROJ для .NET Core](/dotnet/core/tools/csproj).

## <a name="how-the-toolsversion-attribute-works"></a>Принцип действия атрибута ToolsVersion

 При создании проекта в Visual Studio или обновлении существующего проекта атрибут с именем `ToolsVersion` автоматически включается в файл проекта, а его значение соответствует версии MSBuild, включенной в выпуск Visual Studio. Дополнительные сведения см. в статье [Общие сведения о настройке для платформы](../ide/visual-studio-multi-targeting-overview.md).

 Если значение `ToolsVersion` определено в файле проекта, MSBuild использует это значение для определения значений свойств набора инструментов, доступных для проекта. Одно из свойств набора инструментов — это `$(MSBuildToolsPath)`. Оно определяет путь к инструментам .NET Framework. Обязательным является только это свойство набора инструментов (или `$(MSBuildBinPath)`).

 Начиная с Visual Studio 2013, версия набора инструментов MSBuild совпадает с номером версии Visual Studio. MSBuild по умолчанию соответствует этому набору инструментов в Visual Studio и в командной строке, независимо от версии набора инструментов, указанной в файле проекта.  Это поведение можно изменить с помощью флага -ToolsVersion. Дополнительные сведения см. в статье [Переопределение параметров ToolsVersion](../msbuild/overriding-toolsversion-settings.md).

 В следующем примере MSBuild находит файл *Microsoft.CSharp.targets* с помощью зарезервированного свойства `MSBuildToolsPath`.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

 Значение `MSBuildToolsPath` можно изменить, определив пользовательский набор инструментов. Дополнительные сведения см. в статье [Стандартные и настраиваемые конфигурации наборов инструментов](../msbuild/standard-and-custom-toolset-configurations.md).

 Если вы компилируете решение из командной строки и указываете значение атрибута `ToolsVersion` для *msbuild.exe*, все проекты и зависимости между проектами компилируются в соответствии с этим значением `ToolsVersion`, даже если в каждом проекте в решении указано собственное значение `ToolsVersion`. Сведения об определении значения `ToolsVersion` для каждого проекта см. в статье [Переопределение параметров ToolsVersion](../msbuild/overriding-toolsversion-settings.md).

 Атрибут `ToolsVersion` также используется для миграции проектов. Например, если открыть проект Visual Studio 2008 в Visual Studio 2010, то файл проекта обновится и получит значение ToolsVersion = "4.0". Если после этого вы попытаетесь открыть этот проект в Visual Studio 2008, он не распознает обновленное значение атрибута `ToolsVersion` и построит проект таким образом, как если бы этот атрибут по-прежнему имел значение 3.5.

 В Visual Studio 2010 и Visual Studio 2012 используется ToolsVersion 4.0. В Visual Studio 2013 используется ToolsVersion 12.0. Visual Studio 2015 использует ToolsVersion 14.0, а Visual Studio 2017 — ToolsVersion 15.0. Во многих случаях проект можно открыть в нескольких версиях Visual Studio без внесения изменений. В Visual Studio всегда используется правильный набор инструментов, но если версия не совпадает с версией в файле проекта, вы получите уведомление. Почти всегда это предупреждение носит информационный характер, так как наборы инструментов в большинстве случаев совместимы.

 Поднаборы инструментов, описываемые ниже в этом разделе, позволяют MSBuild автоматически переключаться на набор инструментов в зависимости от контекста, в котором запущено построение. Например, при запуске в Visual Studio 2012 MSBuild использует более новый набор инструментов, чем при запуске в Visual Studio 2010, но при этом не требует изменений в файле проекта.

## <a name="toolset-implementation"></a>Реализация набора инструментов

 Реализация набора инструментов осуществляется с помощью выбора путей к различным инструментам, целям и задачам, из которых состоит набор инструментов. Инструменты в наборе, которые определяет MSBuild, поступают из следующих источников:

- из папки .NET Framework;

- из дополнительных управляемых инструментов.

  В число управляемых инструментов входят *ResGen.exe* и *TlbImp.exe*.

MSBuild предлагает два способа доступа к набору инструментов:

- с помощью свойств набора инструментов;

- с помощью методов <xref:Microsoft.Build.Utilities.ToolLocationHelper>.

Свойства набора инструментов указывают на пути к инструментам. Начиная с Visual Studio 2017, система MSBuild больше не имеет фиксированного расположения. По умолчанию она находится в папке *MSBuild\15.0\Bin* относительно папки установки Visual Studio. В более ранних версиях MSBuild определяет местоположение соответствующего раздела реестра в соответствии со значением атрибута `ToolsVersion` в файле проекта, а затем использует сведения из этого раздела для настройки свойств набора инструментов. Например, если атрибут `ToolsVersion` имеет значение `12.0`, MSBuild задает свойства набора инструментов в соответствии с разделом реестра **HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0**.

 Свойства набора инструментов:

- `MSBuildToolsPath` указывает путь к двоичным файлам MSBuild;

- `SDK40ToolsPath` указывает путь к дополнительным управляемым инструментам для MSBuild 4.x (4.0 или 4.5);

- `SDK35ToolsPath` указывает путь к дополнительным управляемым инструментам для MSBuild 3.5.

Вы также можете программно определить набор инструментов, вызвав методы класса <xref:Microsoft.Build.Utilities.ToolLocationHelper>. Класс включает следующие методы:

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A> возвращает путь к папке .NET Framework;

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A> возвращает путь к файлу в папке .NET Framework;

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> возвращает путь к папке управляемых инструментов;

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> возвращает путь к файлу, который обычно находится в папке управляемых инструментов;

- [GetPathToBuildTools](/previous-versions/visualstudio/visual-studio-2013/dn251121(v=vs.121)) возвращает путь к папке инструментов построения.

### <a name="sub-toolsets"></a>Поднаборы инструментов

 В версиях младше 15.0 для указания пути к основным инструментам в MSBuild используется раздел реестра. Если в разделе имеется подраздел, то он используется в MSBuild для указания пути к поднабору инструментов, в котором содержатся дополнительные инструменты. В этом случае набор инструментов определяется комбинацией определений свойств, которые настраиваются в двух разделах.

> [!NOTE]
> Если имена свойств набора инструментов конфликтуют, то значение, определенное для пути подраздела, заменяет значение, установленное для пути корневого раздела.

 Поднаборы инструментов становятся активными в настоящем свойства построения `VisualStudioVersion`. Это свойство может принимать одно из следующих значений:

- "10.0" указывает на поднабор инструментов .NET Framework 4;

- "11.0" указывает на поднабор инструментов .NET Framework 4.5;

- "12.0" указывает на поднабор инструментов .NET Framework 4.5.1;

Поднаборы инструментов 10.0 и 11.0 должны использоваться с ToolsVersion 4.0. В более поздних версиях версии поднабора инструментов и ToolsVersion должны совпадать.

В процессе построения MSBuild автоматически определяет и задает для свойства `VisualStudioVersion` значение по умолчанию, если оно не было установлено ранее.

MSBuild обеспечивает перезагрузку для методов `ToolLocationHelper`, которые добавляют значение перечисления `VisualStudioVersion` в виде параметра.

Поднаборы инструментов впервые появились на платформе .NET Framework 4.5.

## <a name="see-also"></a>См. также

- [Стандартные и настраиваемые конфигурации наборов инструментов](../msbuild/standard-and-custom-toolset-configurations.md)
- [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md)
