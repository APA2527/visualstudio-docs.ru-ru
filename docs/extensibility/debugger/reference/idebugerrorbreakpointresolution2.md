---
title: IDebugErrorBreakpointResolution2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2
helpviewer_keywords:
- IDebugErrorBreakpointResolution2
ms.assetid: b1234216-0ac8-461d-b2a7-54f60f8f3262
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1581e9f00e4a2dcb0a7bdab67cfe601b1c9dd05f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888385"
---
# <a name="idebugerrorbreakpointresolution2"></a>IDebugErrorBreakpointResolution2
Этот интерфейс представляет разрешение ошибки точки останова.

## <a name="syntax"></a>Синтаксис

```
IDebugErrorBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки реализует этот интерфейс в рамках поддержки точек останова. Этот интерфейс используется для сообщения о том, где не удалось выполнить привязку точки останова.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызов [жетбреакпоинтресолутион](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) возвращает этот интерфейс, чтобы предоставить сведения о том, где не удалось привязать точку останова. Метод [жетеррорбреакпоинт](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) получает интерфейс [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugErrorBreakpointResolution2` .

|Метод|Описание|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Возвращает тип точки останова.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Возвращает сведения о разрешении точки останова.|

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
