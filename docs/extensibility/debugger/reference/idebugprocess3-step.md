---
title: 'IDebugProcess3:: шаг | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 69f7c1736f786b2c59678826b71f7f9349629057
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926253"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Заставляет процесс выполнить шаг 1 инструкции или инструкции.

> [!NOTE]
> Этот метод следует использовать вместо [шага](../../../extensibility/debugger/reference/idebugprogram2-step.md).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

## <a name="parameters"></a>Параметры
`pThread`\
окне Объект [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, для которого выполняется пошаговое выполнение.

`sk`\
окне Одно из значений [степкинд](../../../extensibility/debugger/reference/stepkind.md) .

`step`\
окне Одно из значений [степунит](../../../extensibility/debugger/reference/stepunit.md) .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Если существует какая-либо синхронизация потоков или обмен данными между потоками, другие потоки в процессе будут выполняться, когда конкретный поток пошаговым выполнением.

 **Предупреждение об ошибке** Не отправляйте событие остановки или мгновенное (синхронное) событие в [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может перестать отвечать на запросы.

## <a name="see-also"></a>См. также раздел
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
