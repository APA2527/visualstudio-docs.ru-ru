---
title: Метаданные элементов в пакетной обработке целевых объектов | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9dd6c297e00a305fbd1b13cf0fe0bd4a4f151f6b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192873"
---
# <a name="item-metadata-in-target-batching"></a>Метаданные элементов в пакетной обработке целевых объектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] может анализировать зависимости для входных и выходных данных целевого объекта сборки. Если определено, что входные или выходные данные целевого объекта актуальны, он пропускается, а сборка продолжается. Элементы `Target` используют атрибуты `Inputs` и `Outputs`, чтобы задать элементы, обрабатываемые во время анализа зависимостей.  
  
 Если целевой объект содержит задачу, которая использует пакетные элементы в качестве входных и выходных данных, элемент `Target` целевого объекта должен использовать пакетную обработку в своих атрибутах `Inputs` или `Outputs`, чтобы позволить [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] пропускать уже актуальные пакеты элементов.  
  
## <a name="batching-targets"></a>Целевые объекты пакетной обработки  
 Следующий пример содержит список элементов `Res`, который поделен на два пакета на основе метаданные элемента `Culture`. Каждый из пакетов передается в задачу `AL`, которая создает для них по выходной сборке. Используя пакетную обработку для атрибута `Outputs` элемента `Target`, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] может определить, актуальны ли отдельные пакеты, прежде чем запускать целевой объект. Без пакетной обработки целевых объектов оба пакета элементов будут выполняться задачей при каждом запуске целевого объекта.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Res Include="Strings.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Strings.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
    </ItemGroup>  
  
    <Target Name="Build"  
        Inputs="@(Res)"  
        Outputs="%(Culture)\MyApp.resources.dll">  
  
        <AL Resources="@(Res)"  
            TargetType="library"  
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Инкрементное построение](../msbuild/how-to-build-incrementally.md)   
 [Пакетная обработка](../msbuild/msbuild-batching.md)   
 [Элемент Target (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Метаданные элементов в пакетной обработке задач](../msbuild/item-metadata-in-task-batching.md)
