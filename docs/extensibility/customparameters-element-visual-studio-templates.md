---
title: Элемент CustomParameters (шаблоны Visual Studio) | Документация Майкрософт
description: Сведения об элементе CustomParameters и о том, как он группирует пользовательские параметры, которые должны быть переданы мастеру шаблонов, когда мастер выполняет замену параметров.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c78c8a038df33d9b548229966402d0058f53144
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671483"
---
# <a name="customparameters-element-visual-studio-templates"></a>Элемент CustomParameters (шаблоны Visual Studio)
Группирует пользовательские параметры, которые должны быть переданы мастеру шаблонов, когда мастер выполняет замену параметров.

## <a name="syntax"></a>Синтаксис

```
<CustomParameters>
    <CustomParameter/>
    <CustomParameter/>
</CustomParameters>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Содержит имя и значение настраиваемого параметра, используемого при создании проекта или элемента из шаблона. Элемент `CustomParameter` может содержать любое число элементов `CustomParameters`, включая ноль.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Задает содержимое шаблона.|

## <a name="remarks"></a>Remarks

## <a name="example"></a>Пример
 В следующем примере показано, как использовать несколько пользовательских параметров в шаблоне. При создании проекта или элемента на основе шаблона со следующими пользовательскими параметрами все экземпляры `$color1$` и `$color2$` в файлах шаблонов будут заменены на `Red` и `Blue` соответственно.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>См. также раздел
- [Элемент Кустомпараметер (шаблоны Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Параметры шаблона](../ide/template-parameters.md)
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
