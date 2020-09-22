---
title: Элемент Import (MSBuild) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9f8edefc8e097f7ada67041b807231f594774548
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843277"
---
# <a name="import-element-msbuild"></a>Элемент Import (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Импортирует содержимое одного файла проекта в другой файл проекта.  
  
 \<Project>  
 \<Import>  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Import Project="ProjectPath"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Project`|Обязательный атрибут.<br /><br /> Путь к импортируемому файлу проекта. Этот путь может содержать подстановочные знаки. Совпадающие файлы импортируются в отсортированном порядке. С помощью этой функции можно добавить код в проект, просто добавив файл кода в каталог.|  
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Нет  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Обязательный корневой элемент файла проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
|[ImportGroup](../msbuild/importgroup-element.md)|Содержит коллекцию элементов `Import` , сгруппированных по необязательному условию.|  
  
## <a name="remarks"></a>Remarks  
 С помощью элемента `Import` можно повторно использовать код, который является общим для нескольких файлов проекта. Это упрощает обслуживание кода, так как все изменения, внесенные в общий код, распространяются по всем проектам, которые его импортируют.  
  
 По соглашению общие импортируемые файлы проекта сохраняются с расширением TARGETS, но являются стандартными файлами проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] не запрещает импортировать проект с другим расширением файла, однако в целях согласованности рекомендуется использовать расширение TARGETS.  
  
 Относительные пути в импортируемых проектах интерпретируются относительно каталога импортируемого проекта. Таким образом, если файл проекта импортируется в несколько файлов проектов, находящихся в разных расположениях, относительные пути в импортируемом файле проекта будут интерпретироваться по-разному для каждого импортируемого проекта.  
  
 Всем зарезервированным свойствам [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , относящимся к файлу проекта, например `MSBuildProjectDirectory` и `MSBuildProjectFile`, на которые имеются ссылки в импортируемом проекте, значения присваиваются в зависимости от импортируемого файла проекта.  
  
 Если у импортируемого проекта нет атрибута `DefaultTargets` , импортируемые проекты проверяются в порядке импорта и используется значение первого обнаруженного атрибута `DefaultTargets` . Например, если ProjectA импортирует ProjectB и ProjectC (в таком порядке), а ProjectB импортирует ProjectD, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] сначала ищет `DefaultTargets` в ProjectA, затем в ProjectB, затем в ProjectD и наконец в ProjectC.  
  
 Схема импортируемого проекта идентична схеме стандартного проекта. Хотя [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] может быть в состоянии выполнить сборку импортируемого проекта, это маловероятно, так как импортируемый проект обычно не содержит сведения о задании свойств или порядке выполнения целевых объектов. В отношении получения этих сведений импортируемый проект зависит от проекта, в который он импортируется.  
  
> [!NOTE]
> Хотя операторы условного импорта работают в MSBuilds в командной строке, они не работают с MSBuild в интегрированной среде разработки (IDE) [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Проверка условных импортов выполняется с использованием значений конфигурации и платформы, задаваемых при загрузке проекта. Если впоследствии вносятся изменения, требующие перепроверки условий в файле проекта, например изменение платформы, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] повторяет проверку условий для свойств и элементов, но не для импортов. Поскольку условия импорта не перепроверяются, импорт пропускается.  
>   
> Чтобы обойти это, поместите условные импорты в файлы TARGETS или поместите код в условный блок, такой как [Choose Element (MSBuild)](../msbuild/choose-element-msbuild.md) .  
  
## <a name="wildcards"></a>подстановочные знаки;  
 В .NET Framework 4 MSBuild позволяет использовать в атрибуте Project подстановочные знаки. При наличии подстановочных знаков все найденные совпадения сортируются (для обеспечения повторяемости), а затем импортируются в полученном порядке, как если бы он был задан явно.  
  
 Это удобно, если вы хотите предложить точку расширяемости, чтобы кто-то еще мог импортировать файл без явного добавления вами имени файла в импортируемый файл. Для этого Microsoft.Common.Targets содержит следующую строку в начале файла.  
  
```  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  
  
## <a name="example"></a>Пример  
 В следующем примере показан проект, который содержит несколько элементов и свойств и импортирует общий файл проекта.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <resourcefile>Strings.resx</resourcefile>  
  
        <compiledresources>  
            $(O)\$(MSBuildProjectName).Strings.resources  
        </compiledresources>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs" />  
  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
    </ItemGroup>  
  
    <Import Project="$(CommonLocation)\General.targets" />  
</Project>  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)   
 [Как использовать один и тот же целевой объект в нескольких файлах проекта](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
