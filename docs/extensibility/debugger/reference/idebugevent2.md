---
title: IDebugEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ff87d79d45c90a3307d5f28a2aa6109033f4a59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933340"
---
# <a name="idebugevent2"></a>IDebugEvent2
Этот интерфейс используется для передачи критически важных отладочных данных, таких как остановка в точке останова, и некритически важных данных, например сообщения об отладке.

## <a name="syntax"></a>Синтаксис

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) и поставщик пользовательского порта реализуют этот интерфейс на том же объекте, что и все остальные интерфейсы событий.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Используя аргумент идентификатора интерфейса (IID), заданный для [события](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) или [события](../../../extensibility/debugger/reference/idebugportevents2-event.md), диспетчер отладки сеансов (SDM) вызывает [QueryInterface](/cpp/atl/queryinterface) в `IDebugEvent2` интерфейсе для получения соответствующего интерфейса событий.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugEvent2` .

|Метод|Описание|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Возвращает атрибуты для данного события отладки.|

## <a name="remarks"></a>Remarks
 Более конкретные интерфейсы событий, такие как [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), не являются производными от интерфейса IDebugEvent2, но реализуются в виде отдельного интерфейса для того же объекта, что и `IDebugEvent2` .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
