---
title: IDiaSession::findSymbolByRVA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByRVA method
ms.assetid: 14fb2903-b771-44d6-b0a8-44e0097c58ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf6a32284588163aae57d03ec67c69a9f64663b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839229"
---
# <a name="idiasessionfindsymbolbyrva"></a>IDiaSession::findSymbolByRVA
Возвращает тип указанного символа, который содержит, или ближайший к указанным относительный виртуальный адрес (RVA).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findSymbolByRVA ( 
   DWORD        rva,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Параметры
 `rva`

[in] Указывает RVA.

 `symtag`

[in] Найти тип символа. Значения берутся из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) перечисления.

 `ppSymbol`

[out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) извлечь объект, представляющий символ.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример

```C++
IDiaSymbol* pFunc;
pSession->findSymbolByRVA( rva, SymTagFunction, &pFunc );
```

## <a name="see-also"></a>См. также
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)