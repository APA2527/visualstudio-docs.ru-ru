---
title: Элемент PreviewImage (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86ed3e6f438f399547996245531c2848ac7bdb83
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336091"
---
# <a name="previewimage-element-visual-studio-templates"></a>Элемент PreviewImage (шаблоны Visual Studio)
Задает изображение для предварительного просмотра, в качестве имени файла, для предварительного просмотра изображения, которое будет отображаться в любом **новый проект** или **Добавление нового элемента** диалоговое окно.

 \<VSTemplate> \<TemplateData> \<PreviewImage>

## <a name="syntax"></a>Синтаксис

```
<PreviewImage>"filename"</PreviewImage>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет, как он отображается в любом категорию шаблона и **новый проект** или **Добавление нового элемента** диалоговое окно.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Этот текст должен быть строка, представляющая имя файла.

## <a name="remarks"></a>Примечания
 `PreviewImage` — это необязательный элемент.

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)