---
title: IDebugModOpt::GetModOpts | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4cd6042219e03d9e3ca3b6192b49ccfda6881416
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872807"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Возвращает список необязательных модификаторов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetModOpts(
   ULONG  celt,
   BSTR*  rgelt,
   ULONG* pceltFetched
);
```

```csharp
int GetModOpts(
   uint         celt,
   out string[] rgelt,
   ref uint     pceltFetched
);
```

#### <a name="parameters"></a>Параметры
 `celt`

 [in] Число элементов, которые должны быть возвращены.

 `rgelt`

 [out] Возвращает массив, содержащий параметры.

 `pceltFetched`

 [in, out] Количество элементов, возвращаемых в `rgelt` массива.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)