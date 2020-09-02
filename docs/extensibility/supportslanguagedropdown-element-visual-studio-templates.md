---
title: Элемент Суппортслангуажедропдовн (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1230b493fe746a272cf4ca4cffe9d197afd8ba1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699471"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>Элемент SupportsLanguageDropDown (шаблоны Visual Studio)
Указывает, идентичен ли шаблон веб-элемента для нескольких языков и включен ли параметр **Language** в диалоговом окне **Добавление нового элемента** .

 \<VSTemplate> \<TemplateData>
 \<SupportsLanguageDropDown>

## <a name="syntax"></a>Синтаксис

```
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Текст должен иметь значение `true` или `false` , что указывает, доступен ли параметр **язык** в диалоговом окне **Добавление нового элемента** .

## <a name="remarks"></a>Remarks
 Параметр `SupportsLanguageDropDown` является необязательным элементом. Значение по умолчанию — `false`.

 `SupportsLanguageDropDown`Элемент доступен только для шаблонов веб-элементов.

 Если для этого элемента задано значение, то `true` шаблон элемента идентичен для всех языков программирования, а параметр **язык** включен в диалоговом окне **Добавление нового элемента** . Этот параметр позволяет выбрать язык программирования нового элемента, который необходимо создать на основе шаблона.

## <a name="example"></a>Пример
 В следующем примере указывается, чтобы отобразить параметр раскрывающегося списка **язык** .

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также раздел
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
