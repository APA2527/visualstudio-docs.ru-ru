---
title: Конструктор рабочих процессов - конструктор действия Parallel
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79e1e7e48f7ed7e8cd4084805dfae2018a886a82
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002771"
---
# <a name="parallel-activity-designer"></a>Конструктор действия Parallel

Действие <xref:System.Activities.Statements.Parallel> выполняет коллекцию дочерних действий параллельно.

## <a name="the-parallel-activity"></a>Действие Parallel

Действие <xref:System.Activities.Statements.Parallel> хранит свои дочерние действия в коллекции <xref:System.Activities.Statements.Parallel.Branches%2A>. Используйте действие <xref:System.Activities.Statements.Parallel> вместо действия <xref:System.Activities.Statements.Sequence>, если некоторые дочерние действия могут перейти в состояние бездействия.

<xref:System.Activities.Statements.Parallel> Действие имеет <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> свойство, которое содержит пользователя указано выражение Visual Basic. Действие <xref:System.Activities.Statements.Parallel> вычисляет это свойство после завершения каждой ветви кода. Если результат вычисления равен **True**, а затем <xref:System.Activities.Statements.Parallel> действие завершается без выполнения других ветвей. Если <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> не равен значению **True**, а затем <xref:System.Activities.Statements.Parallel> действие завершается после завершения всех его дочерних действий.

### <a name="using-the-parallel-activity-designer"></a>Использование конструктора действия Parallel

Доступ **параллельных** конструктора действий в **поток управления** категории **элементов**.

**Параллельных** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, везде, где обычно помещаются конструкторы, например, внутри **Последовательности** конструктора действий. После его перетаскивания в конструкторе рабочих процессов, он создает <xref:System.Activities.Statements.Parallel> действие, которое по умолчанию содержит <xref:System.Activities.Activity.DisplayName%2A> из **параллельных**

Чтобы добавить действие для <xref:System.Activities.Statements.Parallel.Branches%2A> коллекцию действия parallel, перетащите некоторые другой конструктор из **элементов** и поместите его в треугольник внутри **параллельных** конструктора действий. Треугольники обрамляют действия, которые содержатся в ветвях. Дополнительные действия можно добавить, применяя эту процедуру повторно. Можно ли изменять порядок действий с помощью перетаскивания их в **параллельных** конструктора действий.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Свойства действия Parallel в конструкторе рабочих процессов

В следующей таблице показаны свойства действия Parallel, а также приводится описание их использования в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает понятное отображаемое имя действия конструктора в заголовке. Значение по умолчанию — **параллельных**. Можно при необходимости изменить значение в **свойства** сетки или напрямую в заголовке конструктора действий.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Содержит коллекцию дочерних действий, которые должны быть выполнены.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Вычисляется после завершения какой-либо ветви. Если результат вычисления равен **True**, то запланированные ожидающие выполнения ветви отменяются. Если это свойство не задано или имеет значение **False**, то действие завершается после завершения всех его дочерних действий. Значение по умолчанию — **null**.|

## <a name="see-also"></a>См. также

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)