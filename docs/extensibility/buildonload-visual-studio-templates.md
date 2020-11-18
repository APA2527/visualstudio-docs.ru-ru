---
title: Атрибут и элемент Буилдонлоад (шаблоны Visual Studio)
titleSuffix: ''
description: Сведения об атрибуте и элементе Буилдонлоад, а также о том, как он указывает, следует ли выполнять сборку проекта сразу после его создания.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#BuildOnLoad
helpviewer_keywords:
- BuildOnLoad attribute [Visual Studio Templates]
- BuildOnLoad element [Visual Studio Templates]
ms.assetid: 950f5fc1-d041-4090-9a5c-60844768a4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37df139f890a7717287db675a3a4b7e4b250dbf3
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671609"
---
# <a name="buildonload-attribute-and-element"></a>Атрибут и элемент Буилдонлоад

Указывает, следует ли выполнять сборку проекта сразу после его создания. **Буилдонлоад** — это и атрибут, и элемент.

Иерархия элементов:

```xml
<VSTemplate>
  <TemplateData>
    <BuildOnLoad>
```

## <a name="element-syntax"></a>Синтаксис элемента

```xml
<BuildOnLoad> true/false </BuildOnLoad>
```

## <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение

Для элемента **буилдонлоад** требуется текстовое значение. Текст должен иметь значение `true` или `false` , что указывает, следует ли выполнять сборку проекта сразу после его создания.

## <a name="remarks"></a>Комментарии

**Буилдонлоад** является необязательным атрибутом. Значение по умолчанию — `false`.

## <a name="example"></a>Пример

В следующем примере показаны метаданные для шаблона C#, когда **буилдонлоад** используется как элемент.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildOnLoad>true</BuildOnLoad>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
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

## <a name="see-also"></a>См. также статью

- [BuildProjectOnload, элемент](buildprojectonload-element-visual-studio-templates.md)
- [TemplateContent, элемент](../extensibility/templatecontent-element-visual-studio-templates.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
