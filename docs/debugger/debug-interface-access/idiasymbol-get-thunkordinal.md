---
title: IDiaSymbol::get_thunkOrdinal | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dadfff62502af59652e9113553e13b4942c540f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63401329"
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Извлекает тип преобразователя значения функции.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_thunkOrdinal ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает значение из [перечисление THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) перечисление, указывающее тип преобразователя значения функции.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Примечания
 Данное свойство допустимо только если символ, представленный [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значение `SymTagThunk`.

 «Преобразователь» — это часть кода, который выполняет преобразование между адресное пространство с 32-разрядной памяти (также известный как плоский пространства имен) и 16-разрядное адресное пространство, (известный как сегментированное адресное пространство).

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)