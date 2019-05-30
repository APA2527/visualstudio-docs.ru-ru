---
title: CONTEXT_INFO_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ed50d43061ee714f8f892e03bb164f16e2e33d9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346386"
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
Указывает, какую информацию нужно извлечь о контексте памяти.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
typedef DWORD CONTEXT_INFO_FIELDS;
```

```csharp
public enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
```

## <a name="fields"></a>Поля
`CIF_MODULEURL`\
Инициализация и использование `bstrModuleUrl` поле [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) структуры.

`CIF_FUNCTION`\
Инициализация и использование `bstrFunction` поле `CONTEXT_INFO` структуры.

`CIF_FUNCTIONOFFSET`\
Инициализация и использование `posFunctionOffset` поле `CONTEXT_INFO` структуры.

`CIF_ADDRESS`\
Инициализация и использование `bstrAddress` поле `CONTEXT_INFO` структуры.

`CIF_ADDRESSOFFSET`\
Инициализация и использование `bstrAddressOffset` поле `CONTEXT_INFO` структуры.

`CIF_ALLFIELDS`\
Инициализировать или использовать все поля `CONTEXT_INFO` структуры.

## <a name="remarks"></a>Примечания
Эти значения передаются параметра [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) метод, чтобы указать, какие поля [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) структуры должны быть инициализированы.

Эти флаги также используются для указания поля `CONTEXT_INFO` структуры не используются и допустимым при возвращении структуры.

Эти значения могут объединяться с помощью побитового логического Сложения.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
