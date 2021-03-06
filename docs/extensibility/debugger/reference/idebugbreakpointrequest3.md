---
title: IDebugBreakpointRequest3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d6e42111ca0c8b357a7f8841511cf935694a30b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893065"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Этот интерфейс представляет сведения, необходимые для создания и привязки любого типа точки останова. Это расширение [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Синтаксис

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Диспетчер отладки сеансов (SDM) обычно реализует этот интерфейс.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Модуль отладки (DE) обращается к этому интерфейсу путем вызова [QueryInterface](/cpp/atl/queryinterface) в интерфейсе IDebugBreakpointRequest2, полученном при вызове [креатепендингбреакпоинт](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам, унаследованным от [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), `IDebugBreakpointRequest3` интерфейс предоставляет следующий метод.

|Метод|Описание|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Получает сведения о запросе точки останова, описывающие этот запрос на точку останова.|

## <a name="remarks"></a>Remarks
 Этот интерфейс используется для предоставления дополнительной информации в DE-by [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуре. Эти дополнительные сведения включают в себя идентификатор поставщика DE (в виде идентификатора GUID), имя точки трассировки и имя ограничения точки останова.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
