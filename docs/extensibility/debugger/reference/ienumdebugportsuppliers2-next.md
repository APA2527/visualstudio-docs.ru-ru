---
title: 'IEnumDebugPortSuppliers2:: Next | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::Next
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Next
ms.assetid: e2a2d226-e70b-42c2-bf00-a936517940c8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04f1b428f76198c0bb06ae6d12c58d5f779a0e79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846742"
---
# <a name="ienumdebugportsuppliers2next"></a>IEnumDebugPortSuppliers2::Next
Возвращает следующий набор из перечисления.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Next(
   ULONG                 celt,
   IDebugPortSupplier2** rgelt,
   ULONG*                pceltFetched
);
```

```csharp
int Next(
   uint                  celt,
   IDebugPortSupplier2[] rgelt,
   ref uint              pceltFetched
);
```

## <a name="parameters"></a>Параметры
`celt`\
[in] Количество получаемых элементов. Также указывает максимальный размер `rgelt` массива.

`rgelt`\
[вход, выход] Массив элементов [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) , которые должны быть заполнены.

`pceltFetched`\
заполняет Возвращает количество элементов, фактически возвращаемых в `rgelt` .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если может быть возвращено меньше запрошенного числа элементов; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
