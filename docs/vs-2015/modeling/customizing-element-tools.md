---
title: Настройка средств элемента | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 72457070c63cdf6c76207bd92521ab7944d4318a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199860"
---
# <a name="customizing-element-tools"></a>Настройка средств элемента
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В некоторых определениях DSL единую концепцию представляют группу элементов. Например при создании модели, в котором компонент имеет фиксированный набор портов, всегда требуется порты, которые нужно создать в то же время, как их родительского компонента. Таким образом необходимо настроить средство создания элемента, таким образом, чтобы он создает группу элементов, вместо одного. Для этого можно настроить способ инициализации средства создания элемента.  
  
 Также можно переопределить, что происходит, когда средство перетаскивается на диаграмму или элемент.  
  
## <a name="customizing-the-content-of-an-element-tool"></a>Настройка содержимого средства элемента  
 Каждое средство элемента хранит экземпляр <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), который содержит сериализованную версию одного или нескольких элементов модели, так и ссылки. По умолчанию EGP средства элемента содержит один экземпляр класса, укажите для инструмента. Это можно изменить, переопределив *ваш язык*`ToolboxHelper.CreateElementToolPrototype`. Этот метод вызывается, когда загружается пакет доменного языка.  
  
 Параметр метода является идентификатор класса, который указан в определении DSL. При вызове метода в классе, которые вас интересуют, можно добавить дополнительные элементы в EGP.  
  
 EGP должен включать внедрение связей от одного основного элемента для дочерних элементов. Оно также может включать ссылки на.  
  
 В следующем примере создается главный элемент и два встроенных элементов. Основной класс называется резистор, и он имеет два отношения внедрения для элементов с именем терминалов. Внедрение свойства роли с именами Terminal1 и Terminal2, и оба имеют кратность 1..1.  
  
```  
using Microsoft.VisualStudio.Modeling; ...    
public partial class CircuitDiagramToolboxHelper  
{  
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)  
  {  
    // A case for each tool to customize:    
    if (domainClassId == Resistor.DomainClassId)  
    {  
      // Set up the prototype elements and links:  
      Resistor resistor = new Resistor(store);  
      resistor.Terminal1 = new Terminal(store);   
      resistor.Terminal2 = new Terminal(store);  
      resistor.Terminal1.Name = "T1"; // embedding  
      resistor.Terminal2.Name = "T2"; // embedding  
      // We could also set up reference links.  
  
      // Create an element group prototype for the toolbox:  
      ElementGroup egp = new ElementGroup(store.DefaultPartition);  
      egp.AddGraph(resistor, true);  
      // We do not have to explicitly include embedded children.  
      return egp.CreatePrototype();  
    }  
    // Element tools for other classes:  
    else  
      return base.CreateElementToolPrototype(store, domainClassId);  
  }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Настройка создания и перемещения элементов](../modeling/customizing-element-creation-and-movement.md)
