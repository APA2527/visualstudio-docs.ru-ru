---
title: BP_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_TYPE
helpviewer_keywords:
- BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 02550141fb1857214d5bfd80d5dd86969bec9fba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737789"
---
# <a name="bp_type"></a>BP_TYPE
Указывает, находится ли точка останова в расположении кода, является расположением данных или другим типом точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
typedef DWORD BP_TYPE;
```

```csharp
public enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
```

## <a name="fields"></a>Поля
`BPT_NONE`\
Указывает, что тип точки останова отсутствует.

`BPT_CODE`\
Задает точку останова в коде.

`BPT_DATA`\
Задает точку останова в данных.

`BPT_SPECIAL`\
Указывает точку останова, которая не является ни кодом, ни типом данных. Этот тип является устаревшим и не должен использоваться.

## <a name="remarks"></a>Remarks
Передается в качестве параметра методам [жетбреакпоинттипе](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) и [жетбреакпоинттипе](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)
