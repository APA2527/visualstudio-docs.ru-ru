---
title: Элемент Parameter | Документация Майкрософт
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbf0c25967d84e930ee97a84709c808d3541e733
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263113"
---
# <a name="parameter-element"></a>Элемент Parameter

Содержит сведения о конкретном параметре для задачи, созданной `UsingTask` `TaskFactory`.  Имя элемента — это имя параметра.  Дополнительные сведения см. в статье [Элемент UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask> \<ParameterGroup> \<Parameter>

## <a name="syntax"></a>Синтаксис

```xml
<ParameterGroup ParameterType="SystemType"
    Output="true/false"
    Required="true/false" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты

 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`ParameterType`|Необязательный атрибут.<br /><br /> Тип параметра .NET, например `System.String`.|
|`Output`|Дополнительный логический атрибут.<br /><br /> Если он имеет значение `true`, этот параметр является для задачи параметром вывода. Значение по умолчанию `false`.|
|`Required`|Дополнительный логический атрибут.<br /><br /> Если он имеет значение `true`, этот параметр является для задачи обязательным. Значение по умолчанию `false`.|

### <a name="child-elements"></a>Дочерние элементы

 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Содержит необязательный список параметров, которые будут присутствовать в задаче, созданной `UsingTask` `TaskFactory`.|

## <a name="example"></a>Пример

 В следующем примере показано использование элемента `Parameter`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
             ...
</ParameterGroup>
       <Task Evaluate="true">
       ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
