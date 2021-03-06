---
title: Устранение неполадок и создание журналов по проблемам MSBuild
description: Сведения о том, как диагностировать проблемы сборки в проекте Visual Studio и при необходимости создавать журнал для отправки в корпорацию Майкрософт на изучение.
ms.custom: SEO-VS-2020
ms.date: 06/27/2019
ms.technology: vs-ide-compile
ms.topic: troubleshooting
helpviewer_keywords:
- msbuild logs"
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: d9308bff68a5a5377c025bba5861ac344dcb0326
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880493"
---
# <a name="troubleshoot-and-create-logs-for-msbuild-problems"></a>Устранение неполадок и создание журналов по проблемам MSBuild

С помощью следующих процедур вы сможете диагностировать проблемы сборки в проекте Visual Studio и, при необходимости, создать журнал для отправки в корпорацию Майкрософт на изучение.

## <a name="a-property-value-is-ignored"></a>Значение свойства игнорируется

Если свойству проекта задано определенное значение, но это не отражается в сборке, сделайте следующее:

1. Откройте Командную строку разработчика Visual Studio, соответствующую вашей версии Visual Studio.
1. Заменив значения для пути решения, конфигурации и имени проекта, выполните следующую команду:

    ```cmd
    msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /pp:out.xml MyProject.vcxproj
    ```

    Эта команда создает "предварительно обработанный" файл проекта MSBuild (out.xml). В этом файле можно выполнить поиск по определенному свойству, чтобы узнать, где оно определено.

Последнее определение этого свойства и будет использоваться в сборке. Если свойство задано дважды, второе значение переопределяет первое. Кроме того, MSBuild оценивает проект в несколько этапов:

- элементы PropertyGroup и Import;
- элементы ItemDefinitionGroups;
- элементы ItemGroup;
- Целевые объекты

Следовательно, этапы выполняются в таком порядке:

```xml
<PropertyGroup>
   <MyProperty>A</MyProperty>
</PropertyGroup>
<ItemGroup>
   <MyItems Include="MyFile.txt"/>
</ItemGroup>
<ItemDefinitionGroup>
  <MyItems>
      <MyMetadata>$(MyProperty)</MyMetadata>
  </MyItems>
</ItemDefinitionGroup>
<PropertyGroup>
   <MyProperty>B</MyProperty>
</PropertyGroup>
```

Во время сборки значением MyMetadata для элемента MyFile.txt будет B (не A и не пустое значение).

## <a name="incremental-build-is-building-more-than-it-should"></a>При добавочной сборке выполняются ненужные операции сборки

Если MSBuild без необходимости перестраивает проект или элемент проекта, создайте подробный или двоичный журнал сборки. В журнале можно выполнить поиск по файлу, который был создан или скомпилирован без необходимости. Выходные данные выглядят следующим образом:

```output
  Task "CL"

  Using cached input dependency table built from:

  F:\test\Project1\Project1\Debug\Project1.tlog\CL.read.1.tlog

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ
  Project1.cpp will be compiled because F:\TEST\PROJECT1\PROJECT1\PROJECT1.H was modified at 6/5/2019 12:37:09 PM.

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ

  Write Tracking Logs:
  Debug\Project1.tlog\CL.write.1.tlog
```

Если вы выполняете сборку в среде IDE Visual Studio (с детализацией окна вывода), в **окне вывода** для каждого проекта отображается причина, по которой он неактуален:

```output
1>------ Up-To-Date check: Project: Project1, Configuration: Debug Win32 ------

1>Project is not up-to-date: build input 'f:\test\project1\project1\project1.h' was modified after the last build finished.
```

## <a name="create-a-binary-msbuild-log"></a>Создание двоичного журнала MSBuild

1. Откройте Командную строку разработчика для вашей версии Visual Studio.
1. В окне командной строки выполните приведенные ниже команды. (Используйте только фактические значения конфигурации и проекта.)

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
    ```

    or

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
    ```

Файл Msbuild.binlog будет создан в каталоге, из которого вы запустили MSBuild. Этот файл вы можете найти и просмотреть с помощью [средства просмотра структурированных журналов Msbuild](http://www.msbuildlog.com/).

## <a name="create-a-detailed-log"></a>Создание подробного журнала

1. В главном меню Visual Studio последовательно выберите пункты **Средства** > **Параметры** > **Проекты и решения** >**Сборка и запуск**.
1. В обоих полях со списком для **уровня детализации при сборке проекта MSBuild** выберите **Подробные**. Первый параметр позволяет управлять уровнем детализации сборки в **окне вывода**, а второй — уровнем детализации сборки в файле журнала \<projectname\>.log, который создается в промежуточном каталоге каждого проекта во время сборки.
2. В командной строке разработчика Visual Studio введите одну из этих команд, указав фактические значения для пути и конфигурации:

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln
    ```

    or

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    Файл Msbuild.log будет создан в каталоге, из которого вы запустили MSBuild.

## <a name="see-also"></a>См. также

- [Устранение неполадок в Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
