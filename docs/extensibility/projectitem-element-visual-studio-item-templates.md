---
title: Элемент ProjectItem (шаблоны элементов Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30446b1aa32b31c640a8f56142dc60fcff4a5458
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335998"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>Элемент ProjectItem (шаблоны элементов Visual Studio)
Указывает файл, включенный в шаблон элемента.

> [!NOTE]
> `ProjectItem` Элемент принимает различные атрибуты в зависимости от того, является ли шаблон для проекта или элемента. В этом разделе объясняется `ProjectItem` элемент для элемента. Объяснение `ProjectItem` элемент для шаблонов проектов, см. в разделе [элемент ProjectItem (шаблоны проектов Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md).

 \<VSTemplate > \<TemplateContent > \<ProjectItem >

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

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

| Атрибут | Описание |
|---------------------| - |
| `SubType` | Необязательный атрибут.<br /><br /> Указывает подтип элемента в многофайловый шаблон элемента. Это значение используется для определения редактора, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] будет использовать, чтобы открыть элемент. |
| `CustomTool` | Необязательный атрибут.<br /><br /> Задает CustomTool для элемента в файле проекта. |
| `ItemType` | Необязательный атрибут.<br /><br /> Задает тип элемента для элемента в файле проекта. |
| `ReplaceParameters` | Необязательный атрибут.<br /><br /> Логическое значение, указывающее, имеет ли элемент значения параметров, которые должны быть заменены при создании проекта из шаблона. Значение по умолчанию — `false`. |
| `TargetFileName` | Необязательный атрибут.<br /><br /> Задает имя элемента, который создается из шаблона. Этот атрибут полезен при использовании замены параметров для создания имени элемента. |

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Задает содержимое шаблона.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Объект `string` , представляющий имя файла в шаблоне *ZIP-файл* файл.

## <a name="remarks"></a>Примечания
 `ProjectItem` является необязательным потомком `TemplateContent`.

 `TargetFileName` Атрибут может использоваться для переименования файлов с параметрами. Например если файл *MyFile.vb* существует в корневом каталоге шаблона *ZIP-файл* файл, но требуется файл должен называться на основе имени файла, указанное пользователем в **Добавление нового элемента**  диалоговое окно, можно использовать следующий код XML:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 При создании элемента на основе этого шаблона, имя файла будет основываться на имя, введенное пользователем в **Добавление нового элемента** диалоговое окно. Это полезно в тех случаях, когда создание многофайловых шаблонов элементов. Дополнительные сведения см. в разделе [Практическое руководство. Создание многофайловых шаблонов элементов](../ide/how-to-create-multi-file-item-templates.md) и [параметров шаблона](../ide/template-parameters.md).

## <a name="example"></a>Пример
 В следующем примере показано метаданные для стандартного шаблона элемента для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] класса.

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

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Практическое руководство. Создание многофайловых шаблонов элементов](../ide/how-to-create-multi-file-item-templates.md)
- [Параметры шаблона](../ide/template-parameters.md)