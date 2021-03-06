---
title: IDebugExceptionEvent2::P Асстодебугжее | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 03ce1499863197ed71ef38fcae6a256b1ca319a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933273"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Указывает, должно ли исключение передаваться в отлаживаемую программу при возобновлении выполнения или если исключение должно быть отклонено.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

## <a name="parameters"></a>Параметры
`fPass`\
окне Ненулевое значение ( `TRUE` ), если исключение должно быть передано в программу, отлаживаемой при возобновлении выполнения, или нуль ( `FALSE` ), если исключение должно быть отклонено.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Вызов этого метода фактически не приводит к выполнению кода в отлаживаемой программе. Вызов просто устанавливает состояние для следующего выполнения кода. Например, вызовы метода [канпасстодебугжее](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) могут возвращать `S_OK` [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` для поля задано значение `EXCEPTION_STOP_SECOND_CHANCE` .

 Интегрированная среда разработки может получить событие [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) и вызвать метод [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) . Обработчик отладки (DE) должен иметь поведение по умолчанию для обработки ситуации, если `PassToDebuggee` метод не вызывается.

## <a name="see-also"></a>См. также раздел
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Продолжить](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
