---
title: IDiaSession::findLinesByVA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByVA method
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29f3f714cdcbe529dac98948f6568934a6f508af
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832410"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
Извлекает информация о номере строки для строк, содержащихся в указанный диапазон виртуальных адресов (VA).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findLinesByVA (
    ULONGLONG             va,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Параметры
`va`

[in] Указывает адрес как ва.

`length`

[in] Указывает число байтов из диапазона адресов, чтобы охватить с этим запросом.

`ppResult`

[out] Возвращает [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , содержащий список всех строке номера, охватывают указанный диапазон адресов.

## <a name="example"></a>Пример
В этом примере показана функция, получающий все номера строк, содержащихся в функции, используя функции виртуальный адрес и длину.

```C++
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    ULONGLONG            va;
    ULONGLONG            length;

    if (pFunc->get_virtualAddress ( &va ) == S_OK)
    {
        pFunc->get_length( &length );
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>См. также
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
