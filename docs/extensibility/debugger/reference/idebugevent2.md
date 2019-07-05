---
title: IDebugEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f87184481c5d01e74d284b175078b67f6f2612d1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310600"
---
# <a name="idebugevent2"></a>IDebugEvent2
Этот интерфейс используется для обмена данными критически важная отладочная информация, например, по остановке в точке останова и не являющиеся критически сведения, такие как сообщение отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) и поставщика пользовательского порта реализация этого интерфейса на один и тот же объект как все другие интерфейсы событий.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 С помощью интерфейса IID интерфейса, аргумент, заданный для [событий](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) или [событий](../../../extensibility/debugger/reference/idebugportevents2-event.md), диспетчер отладки сеансов (SDM) вызывает [QueryInterface](/cpp/atl/queryinterface) на `IDebugEvent2` интерфейс для получения интерфейс соответствующее событие.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugEvent2`.

|Метод|Описание|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Получает атрибуты для этого события отладки.|

## <a name="remarks"></a>Примечания
 Интерфейсы более конкретные события, такие как [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), не являющихся производными от интерфейса IDebugEvent2, но вместо этого реализуются как отдельный интерфейс на один и тот же объект как `IDebugEvent2`.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)