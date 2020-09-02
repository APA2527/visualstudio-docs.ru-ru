---
title: Привязка точек останова | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc7f68093432c96d496921ea593b6e936bad8302
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147966"
---
# <a name="binding-breakpoints"></a>Связывание точек останова
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Если пользователь устанавливает точку останова, например, нажав клавишу F9, интегрированная среда разработки формирует запрос и запрашивает создание точки останова в сеансе отладки.  
  
## <a name="setting-a-breakpoint"></a>Установка точки останова  
 Установка точки останова выполняется в два этапа, так как код или данные, затрагиваемые точкой останова, могут быть еще недоступны. Сначала необходимо описать точку останова, а затем, так как код или данные станут доступными, они должны быть привязаны к этому коду или данным следующим образом:  
  
1. Точка останова запрашивается из соответствующих модулей отладки (DEs), а затем точка останова привязывается к коду или данным по мере их появления.  
  
2. Запрос точки останова отправляется в сеанс отладки, который отправляет его всем соответствующим DEs. Любой DE, который выбирает обработку точки останова, создает соответствующую отложенную точку останова.  
  
3. Сеанс отладки собирает ожидающие точки останова и отправляет их обратно в пакет отладки (компонент отладки Visual Studio).  
  
4. Пакет отладки запрашивает в сеансе отладки, чтобы привязать отложенную точку останова к коду или данным. Сеанс отладки отправляет этот запрос всем соответствующим алгоритмам DEs.  
  
5. Если DE может привязать точку останова, он отправляет событие привязки точки останова обратно в сеанс отладки. Если нет, вместо этого отправляется событие ошибки точки останова.  
  
## <a name="pending-breakpoints"></a>Ожидающие точки останова  
 Ожидающая точка останова может быть привязана к нескольким расположениям кода. Например, строка исходного кода для шаблона C++ может быть привязана к каждой последовательности кода, созданной на основе шаблона. Сеанс отладки может использовать событие, связанное с точкой останова, для перечисления контекстов кода, привязанных к точке останова на момент отправки события. Другие контексты кода могут быть привязаны позже, поэтому параметр DE может отправить несколько событий, привязанных к точке останова, для каждого запроса на привязку. Однако DE должен отправить только одно событие ошибки точки останова на каждый запрос привязки.  
  
## <a name="implementation"></a>Реализация  
 Программный пакет отладки вызывает диспетчер отладки сеанса (SDM) и предоставляет ему интерфейс [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) , который заключает в оболочку [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) структуру, которая описывает устанавливаемую точку останова. Хотя точки останова могут быть разными формами, они в конечном итоге разрешаются в код или контекст данных.  
  
 Модель SDM передает этот вызов каждому соответствующему параметру DE, вызывая его метод [креатепендингбреакпоинт](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) . Если метод DE выбирает обработку точки останова, он создает и возвращает интерфейс [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) . Модель SDM собирает эти интерфейсы и передает их обратно в пакет отладки в виде единого `IDebugPendingBreakpoint2` интерфейса.  
  
 Пока события не создавались.  
  
 Затем пакет отладки пытается привязать отложенную точку останова к коду или данным путем вызова [BIND](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), которая реализуется методом de.  
  
 Если точка останова привязана, то параметр DE отправляет в пакет отладки интерфейс событий [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) . Пакет отладки использует этот интерфейс для перечисления всех контекстов кода (или отдельного контекста данных), привязанных к точке останова путем вызова [енумбаундбреакпоинтс](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), который возвращает один или несколько интерфейсов [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) . Интерфейс [жетбреакпоинтресолутион](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) возвращает интерфейс [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) , а [жетресолутионинфо](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) возвращает [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) объединение, содержащее код или контекст данных.  
  
 Если DE не удается привязать точку останова, он отправляет в пакет отладки один интерфейс событий [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) . Пакет отладки Извлекает тип ошибки (ошибка или предупреждение) и информационное сообщение, вызывая [жетеррорбреакпоинт](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), а затем — [жетбреакпоинтресолутион](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) и [жетресолутионинфо](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Он возвращает структуру [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) , содержащую тип ошибки и сообщение.  
  
 Если a Отменяет обработку точки останова, но не может выполнить ее привязку, возвращается ошибка типа `BPET_TYPE_ERROR` . Пакет отладки отвечает, отображая диалоговое окно ошибки, и интегрированная среда разработки помещает восклицательный знак в глиф точки останова слева от строки исходного кода.  
  
 Если a Отменяет обработку точки останова, не может привязывать ее, но может привязывать ее к другому, она возвращает предупреждение. Интегрированная среда разработки реагирует, вставляя глиф вопроса в глиф точки останова слева от строки исходного кода.  
  
## <a name="see-also"></a>См. также:  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
