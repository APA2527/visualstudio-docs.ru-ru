---
title: IDiaTable::get__NewEnum | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::get__NewEnum method
ms.assetid: ee89bba8-5d5c-4a0b-aa0d-1aad56baa380
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c749b87b525ea52593cdfec301fda6987f361c4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62834120"
---
# <a name="idiatablegetnewenum"></a>IDiaTable::get__NewEnum
Извлекает <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> версии этот перечислитель.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает `IUnknown` интерфейс, который представляет <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> версии этот перечислитель.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)