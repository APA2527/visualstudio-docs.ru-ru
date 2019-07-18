---
title: Конструктор рабочих процессов - конструктор действия Pick
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed558c40e932f2148f2240247d19a4fc6df0d06a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63003587"
---
# <a name="pick-activity-designer"></a>Конструктор действия Pick

Действие <xref:System.Activities.Statements.Pick> обеспечивает поток управления на основе событий. Действие выполняет одну из нескольких ветвей в ответ на запускающее событие.

## <a name="the-pick-activity"></a>Действие Pick

Действие <xref:System.Activities.Statements.Pick> содержит коллекцию объектов <xref:System.Activities.Statements.PickBranch>, один из которых действие <xref:System.Activities.Statements.Pick> может выполнить вследствие некоторого входящего события, служащего триггером. Таким образом конструктор рабочих процессов предоставляет моделирование потока управления на основе событий. Каждый участок кода <xref:System.Activities.Statements.PickBranch> содержит триггер <xref:System.Activities.Statements.PickBranch.Trigger%2A> и действие <xref:System.Activities.Statements.PickBranch.Action%2A>. В начале <xref:System.Activities.Statements.Pick> выполнения действия, все действия триггера из <xref:System.Activities.Statements.PickBranch> запланированные элементы. Когда первое действие завершается, планируется соответствующее действие, а все другие действия триггера отменяются.

### <a name="how-to-use-the-pick-activity-designer"></a>Использование конструктора действия подбора

Доступ **выбрать** конструктора действий в **поток управления** категории **элементов**. **Выбрать** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, везде, где обычно помещаются конструкторы, например внутри  **Последовательность** конструктора действий. После его перетаскивания в конструкторе рабочих процессов, он создает <xref:System.Activities.Statements.Pick> действие, которое по умолчанию содержит два пустых <xref:System.Activities.Statements.PickBranch> действия как элементы с именами Branch1 и Branch2. Соответствующие <xref:System.Activities.Statements.PickBranch.DisplayName%2A> значения свойств можно изменить в **PickBranch** заголовке конструктора действий или в **свойства** окна для каждой ветви.

Существует два способа добавления <xref:System.Activities.Statements.PickBranch> действий в коллекцию <xref:System.Activities.Statements.Pick> объект: перетаскивания **PickBranch** конструктора из **элементов** или с помощью контекстного меню изнутри **выбрать** область конструктора. Дополнительные сведения см. в разделе [PickBranch](../workflow-designer/pickbranch-activity-designer.md) раздела. Обратите внимание на то, что единственный элемент, который можно поместить в **выбрать** конструктор операций является **PickBranch** конструктора действий.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Свойства действия Pick в конструкторе рабочих процессов

В следующей таблице показаны свойства <xref:System.Activities.Statements.Pick> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области конструктора.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.Pick> в заголовке. Значение по умолчанию - Pick. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|

## <a name="see-also"></a>См. также

- [Поток управления](../workflow-designer/control-flow-activity-designers.md)
- [Действие Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Использование действия Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)