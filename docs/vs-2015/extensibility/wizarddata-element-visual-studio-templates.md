---
title: Элемент WizardData (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d7cd59266a69140ba2ea5a7fd1d1b0b0c72f14c2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201932"
---
# <a name="wizarddata-element-visual-studio-templates"></a>Элемент WizardData (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Задает пользовательский XML.  
  
 \<VSTemplate >  
 \<WizardData >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<WizardData>  
    <!-- XML to pass to the custom wizard extension -->  
    ...  
</WizardData>  
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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Содержит все метаданные для шаблона проекта, шаблон элемента или комплект для начала работы.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является необязательным.  
  
 Данный текст задает настраиваемый XML для передачи пользовательского мастера модуля, указанного в [WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md) элемент.  
  
## <a name="remarks"></a>Примечания  
 В этом элементе можно указать любой XML. XML передается как параметр расширение пользовательского мастера, позволяя расширение, используемое содержимое данного элемента. Проверка не выполняется на основе этих данных.  
  
 Содержание `WizardData` передается элемент, без изменений, как параметр в словарь строк параметров в `IWizard.RunStarted` метод. Этот параметр называется $WizardData$.  
  
## <a name="example"></a>Пример  
 В следующем примере показано метаданные для стандартного шаблона проекта для [!INCLUDE[csprcs](../includes/csprcs-md.md)] приложения Windows.  
  
```  
<VSTemplate Version="3.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyTemplate</Name>  
        <Description>Template using IWizard extension</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
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
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
    <WizardData>  
        <!-- XML to pass to the custom wizard extension -->  
    </WizardData>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Элемент WizardExtension (шаблоны Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)   
 [Практическое руководство. Использование мастеров для шаблонов проекта](../extensibility/how-to-use-wizards-with-project-templates.md)
