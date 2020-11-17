---
title: Элемент элемент numberofparentcategoriestorollup (шаблоны)
description: Сведения об элементе элемент numberofparentcategoriestorollup и о том, как он указывает количество родительских категорий, которые будут отображать шаблон в диалоговом окне Новый проект.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58c702a70392f4a0330ea51b563570362f51df35
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672415"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>Элемент элемент numberofparentcategoriestorollup (шаблоны Visual Studio)
Указывает число родительских категорий, которые будут отображать шаблон в диалоговом окне **Новый проект** .

 \<VSTemplate> \<TemplateData>
 \<NumberOfParentCategoriesToRollUp>

## <a name="syntax"></a>Синтаксис

```xml
<NumberOfParentCategoriesToRollUp>
1
</NumberOfParentCategoriesToRollUp>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 `integer`Требуется значение.

 Это значение указывает количество родительских категорий, которые будут отображать шаблон в диалоговом окне **Новый проект** .

## <a name="remarks"></a>Комментарии
 Параметр `NumberOfParentCategoriesToRollUp` является необязательным элементом.

## <a name="example"></a>Пример
 В этом примере показаны метаданные для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения Windows. Если шаблон с этими метаданными размещается на двух уровнях папок под узлом верхнего уровня [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] , шаблон будет отображаться в узле верхнего уровня диалогового окна **Новый проект** . Если параметр `NumberOfParentCategoriesToRollUp` не задан, шаблон отображается только на узле, где он физически расположен.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
