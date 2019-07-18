---
title: Конструктор рабочих процессов - конструктора действия Assign
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4179c23cefbf995242288c1e778f9e0413bfe28e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993258"
---
# <a name="assign-activity-designer"></a>Конструктор действий Assign

**Назначить** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Assign> действия.

## <a name="the-assign-activity"></a>Действие Assign

Действие <xref:System.Activities.Statements.Assign> присваивает значение переменной или аргументу.

### <a name="using-the-assign-activity-designer"></a>Использование конструктора действия Assign

**Назначить** конструктора действий можно найти в **примитивы** категории **элементов**, который нажав **элементов**вкладка (Кроме того, выберите **элементов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

**Назначить** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, где каждый раз, если размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Удаление **назначить** конструктора действий создает <xref:System.Activities.Statements.Assign> действие по умолчанию **DisplayName** из назначения. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **назначить** конструктора действий или в **DisplayName** поле таблицы свойств.

### <a name="the-assign-properties"></a>Свойства Assign

В следующей таблице показаны свойства <xref:System.Activities.Statements.Assign> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, и некоторые из них можно изменить на поверхности конструктора рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.Assign>. Значение по умолчанию - Assign. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.Assign.To%2A>|True|Переменная или аргумент, которым присваивается <xref:System.Activities.Statements.Assign.Value%2A>. Значение должно быть допустимым идентификатором Visual Basic. Чтобы задать свойство, введите выражение Visual Basic в **для** поле **назначить** действие конструктора или в сетке свойств.|
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Значение, присваиваемое переменной. Чтобы задать <xref:System.Activities.Statements.Assign.Value%2A>, введите выражение Visual Basic в **значение** поле **назначить** действие конструктора или в сетке свойств.|

## <a name="see-also"></a>См. также

- [Примитивы](../workflow-designer/primitives-activity-designers.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)