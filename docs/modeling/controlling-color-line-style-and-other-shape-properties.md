---
title: Управление цветом, типом линии и другими свойствами фигур
description: Предоставляет сведения об управлении свойствами формы, такими как цвет и стиль линии.
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 68eda84ec014dec2931e2c35a04dec1ed878e6c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861664"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Управление цветом, стилем линий и другими свойствами фигур

Некоторые свойства формы, такие как Color, могут быть "видимыми". Это значит, что свойства могут быть связаны со свойством предметной области фигуры. Другие должны управляться напрямую.

## <a name="exposing-a-property"></a>Предоставление доступа к свойству
 Некоторые свойства формы, такие как Color, могут быть связаны со значением свойства предметной области.

 В определении DSL выберите класс фигуры, соединителя или схемы. В контекстном меню выберите **добавить предоставленный**, а затем выберите нужное свойство, например цвет заливки.

 Теперь фигура имеет свойство предметной области, которое можно задать в программном коде или в качестве пользователя.

## <a name="dynamically-updating-an-exposed-property"></a>Динамическое обновление доступного свойства
 Обычно необходимо сделать предоставляемое свойство зависимым от другого свойства. Например, фигуру может быть назначен красный цвет, если определенное свойство домена меньше нуля. Чтобы сделать эту зависимость, создайте [правило](../modeling/rules-propagate-changes-within-the-model.md). Пример:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```