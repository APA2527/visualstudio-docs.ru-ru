---
title: IDiaDataSource::get_lastError | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34954cd32b350a7c5f9c176deffd9943f8e05100
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554200"
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
Получает имя файла для последней ошибки загрузки.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 pRetVal

[out] Возвращает строку, содержащую имя файла PDB-файл, связанный с последней ошибки загрузки.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает код последней ошибки, из-за операции загрузки. Возвращает `E_INVALIDARG` Если `pRetVal` параметр `NULL`.

## <a name="example"></a>Пример

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>См. также
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)