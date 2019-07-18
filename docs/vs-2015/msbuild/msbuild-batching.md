---
title: Пакетная обработка MSBuild | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d96330c01ab340d4db67694f358717a2dae0bce3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439374"
---
# <a name="msbuild-batching"></a>Пакетная обработка в MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] может разделять списки элементов на разные категории или пакеты на основе метаданных элементов и поочередно выполнять целевой объект или задачу с использованием каждого пакета.  
  
## <a name="task-batching"></a>Пакетная обработка задач  
 Пакетная обработка задач упрощает работу с файлами проекта, позволяя разделить списки элементов на различные пакеты и передать задаче каждый из этих пакетов отдельно. Это означает, что задачу и ее атрибуты для файла проекта можно объявить всего один раз, а запускать ее можно многократно.  
  
 Укажите, что [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] нужно выполнить пакетную обработку с помощью задачи, используя нотацию %(*имя_метаданных_элемента*) в одном из атрибутов задачи. Следующий пример разделяет элемент `Example` на пакеты на основе значения метаданных элемента `Color` и передает их в задачу `MyTask` по отдельности.  
  
> [!NOTE]
> Если вы не ссылаетесь на список элементов в других атрибутах задачи или имя метаданных может быть неоднозначным, можно использовать нотацию %(*коллекция_элементов.имя_метаданных_элемента*), чтобы полностью определить значение метаданных элемента для использования при пакетной обработке.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Более подробные примеры пакетной обработки см. в разделе [Метаданные элементов в пакетной обработке задач](../msbuild/item-metadata-in-task-batching.md).  
  
## <a name="target-batching"></a>Пакетная обработка целевых объектов  
 Перед выполнением целевого объекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] проверяет актуальность его входных и выходных данных. Если как входные, так и выходные данные актуальны, целевой объект пропускается. Если пакетную обработку использует задача, находящаяся внутри целевого объекта, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] нужно определить актуальность входных и выходных данных для каждого пакета элементов. В противном случае целевой объект выполняется при каждой его активации.  
  
 В следующем примере показан элемент `Target`, содержащий атрибут `Outputs` с нотацией %(*имя_метаданных_элемента*). [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] разделит список элементов `Example` на пакеты с учетом метаданных элементов `Color` и проанализирует метки времени выходных файлов для каждого пакета. Если выходные данные пакета не актуальны, выполняется целевой объект. В противном случае он пропускается.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Другой пример пакетной обработки целевых объектов см. в разделе [Метаданные элементов в пакетной обработке целевых объектов](../msbuild/item-metadata-in-target-batching.md).  
  
## <a name="property-functions-using-metadata"></a>Функции свойств с использованием метаданных  
 Пакетной обработкой можно управлять с помощью функций свойств, включающих метаданные. Например, примененная к объекту директива  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 использует <xref:System.IO.Path.Combine%2A> для объединения пути к корневой папке с путем элемента компиляции.  
  
 Функции свойств не могут находиться внутри значений метаданных.  Например, примененная к объекту директива  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 запрещено.  
  
 Дополнительные сведения о функциях свойств см. в разделе [Функции свойств](../msbuild/property-functions.md).  
  
## <a name="see-also"></a>См. также раздел  
 [Элемент ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Дополнительные возможности](../msbuild/msbuild-advanced-concepts.md)
