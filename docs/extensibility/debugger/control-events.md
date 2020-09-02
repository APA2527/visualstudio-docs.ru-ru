---
title: События элемента управления | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2c3ad9c9b63923bdf2f107e7bc582f3c76cd62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739088"
---
# <a name="control-events"></a>События элемента управления
События необходимо отправить во время управляемого выполнения программы. Все события отправляются с помощью интерфейса [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) и имеют атрибуты, требующие реализации метода [IDebugEvent2:: OutAttribute](../../extensibility/debugger/reference/idebugevent2-getattributes.md) .

## <a name="additional-methods"></a>Дополнительные методы
 Для некоторых событий требуется реализация дополнительных методов, как показано ниже.

- Отправка интерфейса [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) при инициализации модуля отладки (de) требует реализации метода [IDebugEngineCreateEvent2::-Engine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) .

- Управление выполнением требует реализации таких событий элемента управления, как интерфейсы [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) и[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) . **IDebugBreakEvent2** требуется только для асинхронных прерываний.

- Для пошагового выполнения функций требуется реализация интерфейса [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) и его методов.

  События, производные от точек останова, должны быть реализованы в интерфейсах [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)и [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) , а также в методах [IDebugBreakpointBoundEvent2:: жетпендингбреакпоинт](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) и [енумбаундбреакпоинтс](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) .

  Асинхронное вычисление выражений требует реализации интерфейса [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) и его методов [IDebugExpressionEvaluationCompleteEvent2:: Express](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[и](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) .

  Для синхронных событий требуется реализация метода [IDebugEngine2:: континуефромсинчронаусевент](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) .

  Чтобы обработчик написал выходные данные в стиле строки, необходимо реализовать метод [IDebugOutputStringEvent2:: GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) .

## <a name="see-also"></a>См. также раздел
- [Контроль выполнения и оценка состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)
