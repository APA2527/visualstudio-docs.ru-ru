---
title: Элемент ButtonText | Документация Майкрософт
description: Элемент ButtonText позволяет указать текст, который отображается в различных меню. Элемент ButtonText не может быть пустым, даже если указаны другие текстовые поля.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b03b5fce58795488f6c379fcf93e5f7fea074e13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927175"
---
# <a name="buttontext-element"></a>ButtonText, элемент
Это поле позволяет указать текст, отображаемый в различных меню. По умолчанию `ButtonText` элемент отображается в контроллерах меню. `ButtonText`Элемент также станет значением по умолчанию, если другие текстовые поля пусты. `ButtonText`Элемент не может быть пустым, даже если указаны другие текстовые поля.

## <a name="syntax"></a>Синтаксис

```xml
<ButtonText>My Command</ButtonText>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент Strings](../extensibility/strings-element.md)|Группирует текстовые элементы, такие как `ButtonText` и `CommandName` .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение `ButtonText` элемента содержит текст, отображаемый для пунктов меню, КомБОС и других элементов пользовательского интерфейса, имеющих видимый текст.

## <a name="see-also"></a>См. также раздел
- [Файлы таблицы команд Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
