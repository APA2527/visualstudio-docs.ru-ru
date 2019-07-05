---
title: Задержка конструктора действий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 528317a97a9b2582442dacfcf9ba8a35943736e8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976715"
---
# <a name="delay-activity-designer"></a>Конструктор действия Delay
**Задержка** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Delay> действия.  
  
## <a name="the-delay-activity"></a>Действие Delay  
 Действие <xref:System.Activities.Statements.Delay> откладывает выполнение рабочего процесса на указанное время.  
  
### <a name="using-the-delay-activity-designer"></a>Использование конструктора действия Delay  
 **Задержка** конструктора действий можно найти в **примитивы** категории **элементов**, который нажав **элементов**вкладке [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **Задержка** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. Будет создано действие <xref:System.Activities.Statements.Delay>, где значение <xref:System.Activities.Activity.DisplayName%2A> по умолчанию равно Delay. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **задержка** конструктора действий или в **DisplayName** поле таблицы свойств.  
  
### <a name="the-delay-properties"></a>Свойства Delay  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Delay> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые ― в области конструктора [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.Delay>. Значение по умолчанию - Delay. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Период времени, на который задерживается выполнение рабочего процесса. Это свойство задается в таблице свойств. Введите литерал <xref:System.TimeSpan> в формате 00:00:00 или выражение Visual Basic для указания периода времени.|  
  
## <a name="see-also"></a>См. также  
 [Примитивы](../workflow-designer/primitives-activity-designers.md)   
 [назначить](../workflow-designer/assign-activity-designer.md)   
 [Конструктор действия Delay](../workflow-designer/delay-activity-designer.md)   
 [Метод InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)