---
title: Элемент VSTemplate (шаблоны Visual Studio) | Документация Майкрософт
description: Сведения об элементе VSTemplate и его том, как он содержит все метаданные о шаблоне проекта, шаблоне элемента или начальном наборе.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 973e2ede7e97d1e7710e6571d520be3d8919b9d9
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903485"
---
# <a name="vstemplate-element-visual-studio-templates"></a>Элемент VSTemplate (шаблоны Visual Studio)
Содержит все метаданные о шаблоне проекта, шаблоне элемента или начальном наборе.

## <a name="syntax"></a>Синтаксис

```csharp
<VSTemplate Type="TemplateType" Version="x.x.x">
    <TemplateData>    </TemplateData>
    <TemplateContent>    </TemplateContent>
    ...
</VSTemplate>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

| Атрибут | Описание |
|-----------| - |
| `Type` | Идентифицирует шаблон как шаблон проекта или шаблон элемента. Этот атрибут может иметь значение `Project` или `Item` . |
| `Version` | Указывает номер версии для шаблона. Шаблоны в [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] и [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] имеют `Version` значение атрибута `3.0.0` . |

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Указывает данные, которые классифицируют шаблон, и определяет, как он отображается в диалоговом окне **Новый проект** или **Добавление нового элемента** .|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Задает содержимое шаблона.|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Необязательный элемент.|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Необязательный элемент.|

### <a name="parent-elements"></a>Родительские элементы
 Нет.

## <a name="remarks"></a>Remarks
 `VSTemplate`Элемент является корневым элементом *VSTEMPLATE* -файлов.

## <a name="example"></a>Пример
 В следующем примере показаны метаданные для шаблона проекта [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs</ProjectItem>
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
