---
title: Элемент IDSymbol | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39ef9d059353f143c80e8956fa14f1812dc90859
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861854"
---
# <a name="idsymbol-element"></a>Элемент IDSymbol
`IDSymbol` Элемент содержит идентификатор GUID: ID пары, который представляет меню, группы или команды. Идентификатор GUID поступает из родительского `GuidSymbol` элемент. `IDSymbol` Элемент имеет `name` атрибут, который содержит понятное имя для идентификатора, который содержится в `value` атрибута.

## <a name="syntax"></a>Синтаксис

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|имя|Обязательный. Имя символа идентификатора.|
|value|Обязательный. Числовое значение идентификатора символа идентификатора.|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент GuidSymbol](../extensibility/guidsymbol-element.md)|Содержит идентификатор GUID пары GUID: ID, который представляет меню, группы или команды. Группирует элементы `IDSymbol`.|

## <a name="remarks"></a>Примечания
 Каждый `IDSymbol` элемент в заданной `GuidSymbol` элемент должен иметь уникальный `value`. Тем не менее `IDSymbol` до тех пор, пока они имеют разные родительские элементы, которые имеют одинаковые значения могут существовать в пакете.

## <a name="see-also"></a>См. также
- [Visual Studio командные файлы table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)