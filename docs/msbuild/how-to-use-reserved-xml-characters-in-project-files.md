---
title: Практическое руководство. Использование резервных символов XML в файлах проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f60b7d2c0de74743c021feee56a3d9f3c8f3eb5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75574331"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Практическое руководство. Использование резервных символов XML в файлах проектов
При создании файлов проекта вам может потребоваться использовать зарезервированные символы XML, например, в значениях свойств или параметров задачи. Однако некоторые зарезервированные символы необходимо заменить именованными сущностями, чтобы файл проекта можно было проанализировать.

## <a name="use-reserved-characters"></a>Использование зарезервированных знаков
 В следующей таблице описаны зарезервированные символы XML, которые требуется заменить именованными сущностями, чтобы файл проекта можно было проанализировать.

|Зарезервированный символ|Именованная сущность|
|------------------------|------------------|
|\<|&amp;lt;|
|>|&amp;gt;|
|&|&amp;amp;|
|"|&amp;quot;|
|'|&amp;apos;|

#### <a name="to-use-double-quotes-in-a-project-file"></a>Использование двойных кавычек в файле проекта

- Замените двойные кавычки соответствующей именованной сущностью &amp;quot;. Например, чтобы заключить в двойные кавычки список элементов `EXEFile`, введите:

    ```xml
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    ```

## <a name="example"></a>Пример
 В следующем примере кода двойные кавычки используются для выделения имени файла в сообщении, выводимом файлом проекта.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>"HelloWorldCS"</appname>
    </PropertyGroup>
    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs" />
    </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input
        files of type CSFile -->
        <Csc Sources = "@(CSFile)">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile"/>
        </Csc>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    </Target>
</Project>
```

## <a name="see-also"></a>См. также
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
