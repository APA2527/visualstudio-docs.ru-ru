---
title: 'IEnumDebugBoundBreakpoints2:: Clone | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2::Clone
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Clone
ms.assetid: c6ce01a2-7da3-46ec-9837-855042fa7244
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e91efb24fec454b509d64decb6b9fd3954c1c9d9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875787"
---
# <a name="ienumdebugboundbreakpoints2clone"></a>IEnumDebugBoundBreakpoints2::Clone
Возвращает копию текущего перечисления как отдельный объект.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Clone(
   IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
[out] Возвращает копию этого перечисления как отдельный объект.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Копия перечисления имеет то же состояние, что и оригинал, во время вызова этого метода. Однако исходное состояние копии и исходного состояния является отдельным и может быть изменено по отдельности.

## <a name="see-also"></a>См. также раздел
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
