---
title: Элемент ProjectItem (шаблоны элементов Visual Studio) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4778603278bf07dc7b0a45544b4835d2ed2cbf8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842377"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>Элемент ProjectItem (шаблоны элементов Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает файл, включенный в шаблон элемента.  
  
> [!NOTE]
> `ProjectItem`Элемент принимает различные атрибуты в зависимости от того, предназначен ли шаблон для проекта или элемента. В этом разделе описывается `ProjectItem` элемент для элемента. Описание `ProjectItem` элемента для шаблонов проектов см. в разделе [элемент ProjectItem (шаблоны проектов Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<ProjectItem>  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`SubType`|Необязательный атрибут.<br /><br /> Указывает подтип элемента в многофайлового шаблона элемента. Это значение используется для определения редактора, который [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] будет использовать для открытия элемента.|  
|`CustomTool`|Необязательный атрибут.<br /><br /> Задает CustomTool для элемента в файле проекта.|  
|`ItemType`|Необязательный атрибут.<br /><br /> Задает значение ItemType для элемента в файле проекта.|  
|`ReplaceParameters`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, содержит ли элемент значения параметров, которые должны быть заменены при создании проекта из шаблона. Значение по умолчанию: `false`.|  
|`TargetFileName`|Необязательный атрибут.<br /><br /> Указывает имя элемента, созданного на основе шаблона. Этот атрибут полезен при использовании замены параметров для создания имени элемента.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Description|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Задает содержимое шаблона.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Значение типа `string` , представляющее имя файла в ZIP-файле шаблона.  
  
## <a name="remarks"></a>Remarks  
 `ProjectItem` является необязательным дочерним элементом `TemplateContent` .  
  
 `TargetFileName`Атрибут может использоваться для переименования файлов с параметрами. Например, если файл `MyFile.vb` существует в корневом каталоге ZIP-файла шаблона, но вы хотите, чтобы имя файла основывалось на имени файла, предоставленного пользователем в диалоговом окне **Добавление нового элемента** , используйте следующий код XML:  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 При создании элемента на основе этого шаблона имя файла будет основываться на имени пользователя, введенном в диалоговом окне **Добавление нового элемента** . Это полезно при создании шаблонов элементов с несколькими файлами. Дополнительные сведения см. [в разделе инструкции. создание многофайловых шаблонов элементов](../ide/how-to-create-multi-file-item-templates.md) и [параметров шаблона](../ide/template-parameters.md).  
  
## <a name="example"></a>Пример  
 В следующем примере показаны метаданные для стандартного шаблона элемента для [!INCLUDE[csprcs](../includes/csprcs-md.md)] класса.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Пошаговое руководство. создание многофайловых шаблонов элементов](../ide/how-to-create-multi-file-item-templates.md)   
 [Параметры шаблона](../ide/template-parameters.md)
