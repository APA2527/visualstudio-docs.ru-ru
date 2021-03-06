---
title: Элемент IDSymbol | Документация Майкрософт
description: 'Элемент IDSymbol содержит идентификатор пары GUID: ID, представляющей меню, группу или команду.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 830324e708ff83fbcbbbdb98d261130e92c7ba00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883198"
---
# <a name="idsymbol-element"></a>IDSymbol, элемент
`IDSymbol`Элемент содержит идентификатор пары GUID: ID, представляющей меню, группу или команду. Идентификатор GUID поступает из родительского `GuidSymbol` элемента. `IDSymbol`Элемент имеет `name` атрибут, который предоставляет понятное имя для идентификатора, содержащегося в `value` атрибуте.

## <a name="syntax"></a>Синтаксис

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|name|Обязательный элемент. Имя символа идентификатора.|
|значение|Обязательный элемент. Числовое значение идентификатора символа идентификатора.|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[GuidSymbol, элемент](../extensibility/guidsymbol-element.md)|Содержит идентификатор GUID пары GUID: ID, представляющей меню, группу или команду. Группирует элементы `IDSymbol`.|

## <a name="remarks"></a>Remarks
 Каждый `IDSymbol` элемент в заданном `GuidSymbol` элементе должен иметь уникальное значение `value` . Однако `IDSymbol` в пакете могут существовать элементы, имеющие одинаковые значения, если они имеют разные родительские объекты.

## <a name="see-also"></a>См. также раздел
- [Файлы таблицы команд Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
