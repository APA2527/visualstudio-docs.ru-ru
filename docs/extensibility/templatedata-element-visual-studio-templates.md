---
title: Элемент TemplateData (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3ce0226286e8cc4623b66c043eb7bd376597118
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699195"
---
# <a name="templatedata-element-visual-studio-templates"></a>Элемент TemplateData (шаблоны Visual Studio)
Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .

 \<VSTemplate> \<TemplateData>

## <a name="syntax"></a>Синтаксис

```
<TemplateData>
    <Name> ... </Name>
    <Description> ... </Description>
    <Icon> ... </Icon>
    <ProjectType> ... </ProjectType>
    ...
</TemplateData>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы

| Элемент | Описание |
| - | - |
| [Имя](../extensibility/name-element-visual-studio-templates.md) | Обязательный элемент.<br /><br /> Задает имя шаблона в том виде, в каком оно отображается в диалоговом окне **Новый проект** или **Добавление нового элемента** . |
| [Описание](../extensibility/description-element-visual-studio-templates.md) | Обязательный элемент.<br /><br /> Задает описание шаблона в том виде, в каком оно отображается в диалоговом окне **Новый проект** или **Добавление нового элемента** . |
| [Значок](../extensibility/icon-element-visual-studio-templates.md) | Обязательный элемент.<br /><br /> Задает путь и имя файла изображения, который выступает в качестве значка, который отображается в диалоговом окне **Новый проект** или **Добавление нового элемента** для шаблона. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Обязательный элемент.<br /><br /> Классификация шаблона проекта, чтобы он появился в указанной группе в диалоговом окне **Новый проект** . |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Классифицирует шаблон проекта, чтобы он появился в указанной подкатегории в диалоговом окне **Новый проект** . |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает идентификатор шаблона. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает идентификатор группы шаблонов. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Задает значение, используемое для упорядочения шаблона (помимо других шаблонов в той же категории), которое отображается в диалоговом окне **Создание проекта** или **Добавление нового элемента** . |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает, создается ли содержащая папка при создании экземпляра проекта. |
| [дефаултнаме](../extensibility/defaultname-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает имя, которое будет создавать система проектов Visual Studio для проекта или элемента при его создании. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает, будет ли система проектов Visual Studio создавать имя по умолчанию для проекта или элемента при его создании. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает, можно ли создать проект как временный проект (только для Visual Studio 2017). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает, доступна ли кнопка " **Обзор** " в диалоговом окне " **Новый проект** ", чтобы пользователи могли легко изменять каталог по умолчанию, в котором сохранен новый проект. |
| [Скрыта](../extensibility/hidden-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает, отображается ли шаблон в диалоговом окне " **Новый проект** " или " **Добавление нового элемента** ". |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает число родительских категорий, которые будут отображать шаблон в диалоговом окне **Новый проект** . |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Необязательный элемент. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | Необязательный элемент.<br /><br /> Указывает, будет ли текстовое поле **Расположение** в диалоговом окне **Новый проект** быть включено, отключено или скрыто для шаблона проекта. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Используйте этот элемент, если шаблон поддерживает только определенную минимальную версию, а более поздние версии .NET Framework. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает, поддерживает ли шаблон главную страницу для веб-проектов. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает, поддерживает ли шаблон разделение кода или модель страницы кода программной части для веб-проектов. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает, идентичен ли шаблон для нескольких языков и доступен ли параметр **язык** в диалоговом окне **Новый проект** . |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Задает платформу, для которой предназначен шаблон проекта. Этот элемент указывает, что шаблон проекта используется для создания [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] приложений. |

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Содержит все метаданные для шаблона проекта, шаблона элемента или начального набора.|

## <a name="remarks"></a>Remarks
 `TemplateData` является обязательным элементом.

 Если не включить необязательный элемент, используется значение по умолчанию для этого элемента.

## <a name="example"></a>Пример
 В следующем примере показаны метаданные для шаблона проекта [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения.

```
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
