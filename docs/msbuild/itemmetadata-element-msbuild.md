---
title: Элемент ItemMetadata (MSBuild) | Документация Майкрософт
description: Сведения об элементе ItemMetadata MSBuild, содержащем определяемый пользователем ключ метаданных элемента со значением метаданных.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aba274068d8cba4f22526fdefac36d6c75f9f1e2
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903598"
---
# <a name="itemmetadata-element-msbuild"></a>Элемент ItemMetadata (MSBuild)

Содержит определяемый пользователем ключ метаданных элемента, содержащий значение метаданных элемента. Элемент может иметь любое число пар метаданных "ключ — значение".

 \<Project> \<ItemGroup>
 \<Item>

## <a name="syntax"></a>Синтаксис

```xml
<ItemMetadataName> Item Metadata value</ItemMetadataName>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты

 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Дочерние элементы

 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент](../msbuild/item-element-msbuild.md)|Определяемый пользователем элемент, задающий входные данные для процесса сборки.|

## <a name="text-value"></a>Текстовое значение

 Текстовое значение является необязательным.

 Этот текст задает для элемента значение метаданных, которое может быть текстом или XML-документом.

## <a name="example"></a>Пример

 Следующий пример кода демонстрирует добавление метаданных `Culture` со значением `fr` к элементу `CSFile`.

```xml
<ItemGroup>
    <CSFile Include="main.cs" >
        <Culture>fr</Culture>
    </CSFile>
</ItemGroup>
```

## <a name="see-also"></a>См. также

- [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
- [Элементы](../msbuild/msbuild-items.md)
