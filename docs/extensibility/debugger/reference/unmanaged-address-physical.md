---
title: UNMANAGED_ADDRESS_PHYSICAL | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_PHYSICAL
helpviewer_keywords:
- UNMANAGED_ADDRESS_PHYSICAL structure
ms.assetid: fed09686-caa6-4efc-851e-a0432019e9d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 736ef56a67247bac53f1f27f84c994a1bf117b9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880077"
---
# <a name="unmanaged_address_physical"></a>UNMANAGED_ADDRESS_PHYSICAL
Эта структура представляет физический адрес.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagUNMANAGED_ADDRESS_PHYSICAL {
   ULONGLONG offset;
} UNMANAGED_ADDRESS_PHYSICAL;
```

```csharp
public struct UNMANAGED_ADDRESS_PHYSICAL {
   public ulong offset;
}
```

## <a name="members"></a>Члены
 `offset`\
 64-битное смещение в физическом адресном пространстве.

## <a name="remarks"></a>Remarks
 Эта структура является частью объединения в структуре [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , если `dwKind` поле `DEBUG_ADDRESS_UNION` структуры имеет `ADDRESS_KIND_UNMANAGED_PHYSICAL` значение (Value из перечисления [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
