---
title: Метаданные элементов в пакетной обработке задач | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 15a6eeea6ebf75513419cc763b2e29a6b6264391
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843136"
---
# <a name="item-metadata-in-task-batching"></a>Метаданные элементов в пакетной обработке задач
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] может разделять списки элементов на разные категории или пакеты на основе метаданных элементов и поочередно выполнять задачи с использованием каждого пакета. Не так просто понять, какие именно элементы передаются с каким пакетом. В этом разделе рассматриваются наиболее распространенные сценарии, в которых используется пакетная обработка.  
  
- Разделение списка элементов на пакеты  
  
- Деление нескольких списков элементов на пакеты  
  
- Пакетная обработка одного элемента за раз  
  
- Фильтрация списков элементов  
  
  Дополнительные сведения о пакетной обработке с помощью [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] см. в статье [Пакетная обработка в MSBuild](../msbuild/msbuild-batching.md).  
  
## <a name="dividing-an-item-list-into-batches"></a>Разделение списка элементов на пакеты  
 Пакетная обработка позволяет разделить список элементов на различные пакеты на основе метаданных элементов и передать задаче каждый из пакетов отдельно. Это полезно при создании вспомогательных сборок.  
  
 В следующем примере показано, как разделить список элементов на пакеты на основе метаданных элементов. Список элементов `ExampColl` делится на три пакета на основе метаданных элементов `Number`. Если в атрибуте `Text` есть `%(ExampColl.Number)`, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] получает уведомление о том, что необходимо выполнить пакетную обработку. Список элементов `ExampColl` делится на три пакета на основе метаданных `Number`, а каждый пакет отдельно передается задаче.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 [Задача Message](../msbuild/message-task.md) отображает следующие сведения:  
  
 `Number: 1 -- Items in ExampColl: Item1;Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2;Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3;Item6`  
  
## <a name="dividing-several-item-lists-into-batches"></a>Деление нескольких списков элементов на пакеты  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] может разделить несколько списков элементов на пакеты на основе одинаковых метаданных. Это упрощает деление различных списков элементов на пакеты для создания нескольких сборок. Например, у вас может быть список элементов с CS-файлами, разделенный на пакет приложения и пакет сборки, и список элементов с файлами ресурсов, разделенный на пакет приложения и пакет сборки. Затем, используя пакетную обработку, можно передать эти списки элементов одной задаче и создать приложение и сборку.  
  
> [!NOTE]
> Если в передаваемом задаче списке элементов нет элементов с указанными метаданными, каждый элемент из этого списка передается во все пакеты.  
  
 В следующем примере показано, как разделить несколько списков элементов на пакеты на основе метаданных элементов. Списки элементов `ExampColl` и `ExampColl2` делятся на три пакета на основе метаданных элементов `Number`. Если в атрибуте `Text` есть `%(Number)`, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] получает уведомление о том, что необходимо выполнить пакетную обработку. Списки элементов `ExampColl` и `ExampColl2` делятся на три пакета на основе метаданных `Number`, а каждый пакет отдельно передается задаче.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
  
        <ExampColl2 Include="Item4">  
            <Number>1</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item5">  
            <Number>2</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item6">  
            <Number>3</Number>  
        </ExampColl2>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>  
    </Target>  
  
</Project>  
```  
  
 [Задача Message](../msbuild/message-task.md) отображает следующие сведения:  
  
 `Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`  
  
## <a name="batching-one-item-at-a-time"></a>Пакетная обработка одного элемента за раз  
 Пакетная обработка может также выполняться со стандартными метаданными, назначенными каждому элементу при создании. Это гарантирует, что каждый элемент в коллекции будет содержать некоторые метаданные для пакетной обработки. Значение метаданных `Identity` уникально для каждого элемента и используется для его выделения из списка элементов в отдельный пакет. Полный список стандартных метаданных элементов см. в разделе [стандартные метаданные элементов](../msbuild/msbuild-well-known-item-metadata.md).  
  
 Следующий пример демонстрирует поочередную пакетную обработку каждого элемента из списка элементов. Так как значение метаданных `Identity` каждого элемента является уникальным, список элементов `ExampColl` делится на шесть пакетов, каждый из которых содержит один элемент из списка элементов. Если в атрибуте `Text` есть `%(Identity)`, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] получает уведомление о том, что необходимо выполнить пакетную обработку.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1"/>  
        <ExampColl Include="Item2"/>  
        <ExampColl Include="Item3"/>  
        <ExampColl Include="Item4"/>  
        <ExampColl Include="Item5"/>  
        <ExampColl Include="Item6"/>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Identity: "%(Identity)" -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 [Задача Message](../msbuild/message-task.md) отображает следующие сведения:  
  
```  
Identity: "Item1" -- Items in ExampColl: Item1  
Identity: "Item2" -- Items in ExampColl: Item2  
Identity: "Item3" -- Items in ExampColl: Item3  
Identity: "Item4" -- Items in ExampColl: Item4  
Identity: "Item5" -- Items in ExampColl: Item5  
Identity: "Item6" -- Items in ExampColl: Item6  
```  
  
## <a name="filtering-item-lists"></a>Фильтрация списков элементов  
 Пакетную обработку можно использовать для фильтрации определенных элементов из списка элементов перед их передачей задаче. Например, фильтрация по значению известных метаданных элементов `Extension` позволяет выполнить задачу только для файлов с определенным расширением.  
  
 В приведенном ниже примере показано, как разделить список элементов на пакеты на основе метаданных элементов, а затем отфильтровать эти пакеты при передаче их задаче. Список элементов `ExampColl` делится на три пакета на основе метаданных элементов `Number`. Атрибут задачи `Condition` указывает, что задаче будут переданы только пакеты со значением метаданных элемента `Number` равным `2`.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
  
    </ItemGroup>  
  
    <Target Name="Exec">  
        <Message  
            Text = "Items in ExampColl: @(ExampColl)"  
            Condition="'%(Number)'=='2'"/>  
    </Target>  
  
</Project>  
```  
  
 [Задача Message](../msbuild/message-task.md) отображает следующие сведения:  
  
```  
Items in ExampColl: Item2;Item5  
```  
  
## <a name="see-also"></a>См. также:  
 [Стандартные метаданные элементов](../msbuild/msbuild-well-known-item-metadata.md)   
 [Элемент Item (MSBuild)](../msbuild/item-element-msbuild.md)   
 [Элемент ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Пакетной обработки](../msbuild/msbuild-batching.md)   
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)   
 [Справочник по MSBuild](../msbuild/msbuild-reference.md)
