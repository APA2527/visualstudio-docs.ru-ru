---
title: Элемент Кустомдатасигнатуре (шаблоны Visual Studio) | Документация Майкрософт
description: Сведения об элементе Кустомдатасигнатуре и о том, как он указывает текстовую подпись для нахождение пользовательских данных.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e5f42b3c5fe1dc5b9ab9697275876509eb0f8509
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946063"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>Элемент Кустомдатасигнатуре (шаблоны Visual Studio)
Задает текстовую подпись для нахождение пользовательских данных.

 \<VSTemplate> \<TemplateData>
 \<CustomDataSignature>

## <a name="syntax"></a>Синтаксис

```
<CustomDataSignature>"string"</CustomDataSignature>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Классификация шаблона и определение его отображения в диалоговом окне " **Новый проект** " или " **Добавление нового элемента** ".|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Текст — это строка, которая содержит текстовую подпись, необходимую для нахождение пользовательских данных.

## <a name="remarks"></a>Remarks
 Параметр `CustomDataSignature` является необязательным элементом.

## <a name="see-also"></a>См. также раздел
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
