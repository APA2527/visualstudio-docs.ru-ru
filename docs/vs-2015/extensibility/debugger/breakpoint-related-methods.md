---
title: Методы, связанные с точки останова | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47ba1529521fdce042512a38d32ad2ca2eb3cb82
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146442"
---
# <a name="breakpoint-related-methods"></a>Методы, связанные с точкой останова
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отладчик (DE) должны поддерживать параметр точек останова. Отладка в Visual Studio поддерживает следующие типы точек останова:  
  
- привязан  
  
     Запрошенный с помощью пользовательского интерфейса и успешно привязанным к указанной кодовой точке  
  
- Не завершен  
  
     Запрошенный с помощью пользовательского интерфейса, но не привязана к фактическое инструкции  
  
## <a name="discussion"></a>Обсуждение  
 Например ожидающая точка останова происходит при инструкции еще не загружены. Когда он был загружен, ожидающих точек останова try для привязки к коду в указанном расположении, то есть, для вставки разрыва инструкций в коде. События отправляются диспетчер отладки сеансов (SDM) для указания успешной привязки или для уведомления о том, что произошли ошибки привязки.  
  
 Ожидающая точка останова также управляет свой собственный внутренний список соответствующих связанных точек останова. Один ожидающий точка останова может привести к вставки много точек останова в коде. Отладки пользовательского интерфейса Visual Studio показано древовидное представление ожидающих точек останова и соответствующие им привязку точки останова.  
  
 Создание и использование ожидающих точек останова требуется реализация [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) метода, а также следующие методы класса [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) интерфейсов.  
  
|Метод|Описание|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Определяет, является ли заданное ожидающих точек останова можно привязать к расположение кода.|  
|[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Привязывает указанный ожидающие точки останова в одно или несколько расположений кода.|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Получает состояние ожидающая точка останова.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Получает запрос, точки останова, используемый для создания ожидающая точка останова.|  
|[Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Переключает состояние выполнения ожидающая точка останова.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Перечисляет все точки останова, привязанный из ожидающая точка останова.|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Перечисляет все точки останова ошибки, возникающие в результате ожидающая точка останова.|  
|[Удаление](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Удаляет точку останова и все точки останова, привязанный из него.|  
  
 Для перечисления связанных точек останова и точек останова ошибок, должен реализовывать все методы объекта [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) и [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 Ожидающих точек останова, которые привязаны к код расположение требуют реализации следующих [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Получает ожидающая точка останова, содержащей точку останова.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Получает состояние связанная точка останова.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Получает разрешение точек останова, описывающий точку останова.|  
|[Enable](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Включает или отключает точку останова.|  
|[Удаление](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Удаляет связанная точка останова.|  
  
 Разрешение и запроса информации требуют реализации следующих [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Получает тип точки останова, представленный разрешением.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Возвращает сведения о разрешении точки останова, описывающий точку останова.|  
  
 Устранение ошибок, которые могут возникнуть во время привязки требует реализации следующих [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Получает ожидающая точка останова, содержащий точку останова ошибок.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Получает значение разрешения ошибки точки останова, описывающий точку останова ошибок.|  
  
 Устранение ошибок, которые могут возникнуть во время привязки также требует следующих методов класса [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Получает тип точки останова.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Возвращает сведения о разрешении точки останова.|  
  
 Просмотр исходного кода в точке останова, необходимо реализовать методы [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) и/или методы [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент управления выполнением и анализ состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)
