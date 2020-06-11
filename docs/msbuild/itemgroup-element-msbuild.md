---
title: Элемент ItemGroup (MSBuild) | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c058a5986f72192a86d0e554d9e0d0b9bdce1b42
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173516"
---
# <a name="itemgroup-element-msbuild"></a>Элемент ItemGroup (MSBuild)

Содержит набор определенных пользователем элементов [Item](../msbuild/item-element-msbuild.md). Каждый элемент, используемый в проекте MSBuild, должен быть указан как дочерний для элемента `ItemGroup`.

\<Project>
\<ItemGroup>

## <a name="syntax"></a>Синтаксис

```xml
<ItemGroup Condition="'String A' == 'String B'"
           Label="Label">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты

В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Condition`|Необязательный атрибут. Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|
|`Label`|Необязательный атрибут. Идентифицирует `ItemGroup`.|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент](../msbuild/item-element-msbuild.md)|Входные данные для процесса сборки. Любое количество элементов `Item` (может быть ни одного) может содержаться в `ItemGroup`.|

### <a name="parent-elements"></a>Родительские элементы

| Элемент | Описание |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Обязательный корневой элемент файла проекта MSBuild. |
| [Целевой объект](../msbuild/target-element-msbuild.md) | Начиная с версии .NET Framework 3.5, элемент `ItemGroup` может находиться внутри элемента `Target`. Дополнительные сведения см. в разделе [Целевые объекты](../msbuild/msbuild-targets.md). |

## <a name="example"></a>Пример

В следующем примере кода показаны определяемые пользователем элементы коллекций `Res` и `CodeFiles`, объявленные внутри элемента `ItemGroup`. Каждый элемент в коллекции `Res` содержит определяемый пользователем дочерний элемент [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Res Include = "Strings.fr.resources" >
            <Culture>fr</Culture>
        </Res>
        <Res Include = "Dialogs.fr.resources" >
            <Culture>fr</Culture>
        </Res>

        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />
        <CodeFiles Include="..\..\Resources\Constants.cs" />
    </ItemGroup>
...
</Project>
```

В файле простого проекта обычно присутствует один элемент `ItemGroup`, однако при необходимости можно использовать несколько элементов `ItemGroup`. Если используется несколько элементов `ItemGroup`, они объединяются в один элемент `ItemGroup`. Например, некоторые элементы могут быть включены с использованием отдельного элемента `ItemGroup`, который определяется в импортируемом файле.

Для элементов ItemGroup могут применяться условия с помощью атрибута `Condition`. В этом случае элементы добавляются в список элементов только при соблюдении условия. См. [Условия MSBuild](msbuild-conditions.md).

## <a name="see-also"></a>См. также

- [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
- [Элементы](../msbuild/msbuild-items.md)
- [Общие элементы проектов MSBuild](../msbuild/common-msbuild-project-items.md)
