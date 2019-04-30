---
title: IDebugSymbolProvider::GetMethodFieldsByName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName
helpviewer_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName method
ms.assetid: 1f781320-81ef-4037-b068-f1864b271258
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8609452919b5f2c2c3f94a7ef3853e1559b33e77
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915746"
---
# <a name="idebugsymbolprovidergetmethodfieldsbyname"></a>IDebugSymbolProvider::GetMethodFieldsByName
Этот метод возвращает поле, представляющее полному имени метода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMethodFieldsByName( 
   LPCOLESTR          pszFullName,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int GetMethodFieldsByName(
   string               pszFullName,
   NAME_MATCH           nameMatch,
   out IEnumDebugFields ppEnum
);
```

#### <a name="parameters"></a>Параметры
 `pszFullName`

 [in] Имя метода.

 `nameMatch`

 [in] Выбирает тип соответствия, например, с учетом регистра.

 `ppEnum`

 [out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) перечислитель для полей, связанных с помощью этого метода.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Метод можно связать с несколькими полями, если он перегружен, например.

## <a name="see-also"></a>См. также
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)