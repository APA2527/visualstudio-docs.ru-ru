---
title: 'IDebugProcess3:: Жетенкаваилаблестате | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dce751223c4513733c5cd9ce815155b7f659b54a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915273"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Этот метод возвращает текущее состояние изменения и продолжения процесса. Пользовательский поставщик порта всегда должен возвращать значение `E_NOTIMPL` .

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetENCAvailableState(
   EncUnavailableReason* pReason
);
```

```csharp
int GetENCAvailableState(
   EncUnavailableReason[] pReason
);
```

## <a name="parameters"></a>Параметры
`pReason`\
заполняет Значение из перечисления [енкунаваилаблереасон](../../../extensibility/debugger/reference/encunavailablereason.md) .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

> [!NOTE]
> Пользовательский поставщик порта всегда должен возвращать значение `E_NOTIMPL` .

## <a name="remarks"></a>Remarks
 На это состояние может повлиять [дисаблинк](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md).

## <a name="see-also"></a>См. также раздел
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
