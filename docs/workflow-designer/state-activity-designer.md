---
title: Конструктор действий конструктор рабочих процессов состояния
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: f1a95808ec19edba01b266ccd280603bcc4321dc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593152"
---
# <a name="state-activity-designer"></a>Конструктор State Activity

<xref:System.Activities.Statements.State> представляет состояние, в котором может находиться конечный автомат.

## <a name="using-the-state-activity-designer"></a>Использование конструктора действий состояний

Чтобы добавить <xref:System.Activities.Statements.State> в рабочий процесс, перетащите конструктор действий **состояния** из раздела **конечный автомат** **области элементов** и поместите его в действие <xref:System.Activities.Statements.StateMachine> на поверхности конструктор рабочих процессов. Действие <xref:System.Activities.Statements.State> можно сбросить в <xref:System.Activities.Statements.StateMachine> и переходы, добавленные позже. Переход также можно создать при помещении действия <xref:System.Activities.Statements.State> на поверхность. Чтобы добавить действие <xref:System.Activities.Statements.State> и создать переход за один шаг, перетащите действие **State** из раздела **конечный автомат** **области элементов** и наведите его на другое состояние в конструкторе рабочих процессов. При наведении <xref:System.Activities.Statements.State> на другое <xref:System.Activities.Statements.State> вокруг другого <xref:System.Activities.Statements.State> будут отображены четыре треугольника. Если объект <xref:System.Activities.Statements.State> бросить в один из четырех треугольников, он будет добавлен к конечному автомату, а также будет добавлен переход состояния из исходного <xref:System.Activities.Statements.State> в сброшенное целевое <xref:System.Activities.Statements.State>. Дополнительные сведения см. в разделе [Переход](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Свойства действия состояния в конструкторе рабочих процессов

В следующей таблице приведены свойства <xref:System.Activities.Statements.State>, которые можно задать с помощью конструктора рабочих процессов, и описано их использование в конструкторе. Некоторые из этих свойств можно изменить в таблице свойств, а некоторые из них ― в области конструктора.

|Имя свойства|Обязательное|Метрики|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Ложь|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.State> в заголовке. Значение по умолчанию — **State**. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций. <xref:System.Activities.Statements.State.DisplayName%2A> используется в строке навигатора, которая отображается в верхней части конструктора рабочих процессов.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Statements.State.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.State.Entry%2A>|Ложь|Указывает действие, которое выполняется при переходе в это состояние. При развертывании действия <xref:System.Activities.Statements.State> это значение можно задать, перетащив действие из **панели элементов** в раздел **записи** состояния.|
|<xref:System.Activities.Statements.State.Exit%2A>|Ложь|Указывает действие, которое выполняется при переходе из этого состояния. Когда <xref:System.Activities.Statements.State> действие разворачивается, это значение можно задать, перетащив действие из **панели элементов** в раздел **Exit** состояния.|
|<xref:System.Activities.Statements.State.Transitions%2A>|Ложь|Перечисляет возможные переходы, исходящие из <xref:System.Activities.Statements.State>. Каждый элемент в списке имеет соединение со связанным <xref:System.Activities.Statements.Transition> и назначение <xref:System.Activities.Statements.State>. При щелчке по ссылке конструктор переключится в расширенное представление для <xref:System.Activities.Statements.Transition> или <xref:System.Activities.Statements.State>.|

## <a name="see-also"></a>См. также:

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)
