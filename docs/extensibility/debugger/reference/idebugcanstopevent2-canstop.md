---
title: IDebugCanStopEvent2::CanStop | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c41c9fda7cc4a169c905dae799ec6cb58c2e3c9
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203173"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Уведомляет отладчик (DE), ли отменить в текущем положении кода или просто продолжить выполнение.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>Параметры
`fCanStop`\
[in] Ненулевое значение (`TRUE`) Если DE остановки в текущее расположение кода; в противном случае — нуль (`FALSE`).

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Получатель этого события обычно не вызывает [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) метод, чтобы определить причину DE хочет остановить, а затем вызывает `IDebugCanStopEvent2::CanStop` метод с соответствующий ответ.

 Если перестает DE, он отправляет событие, описывающее причину остановки. Обычно существуют два события, которые отправляются разрыв пользователя или сигнала, представленный [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) интерфейса и событие точки останова, представленный [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) интерфейс.

## <a name="see-also"></a>См. также
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)