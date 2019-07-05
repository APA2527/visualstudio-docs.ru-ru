---
title: IDiaSession::findFileById | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3454ff5ef087b67dda5d48849d4a6c4eceb7e52
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839359"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Извлекает исходный файл, идентификатор файла источника.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>Параметры
 `uniqueId`

[in] Задает идентификатор исходного файла.

 `ppResult`

[out] Возвращает [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) извлечь объект, представляющий исходный файл.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Идентификатор файла источника — это уникальное значение, используется внутренним образом для пакета SDK для доступа к интерфейсу отладки, чтобы сделать уникальным все исходные файлы. Этот метод обычно используется внутренне для пакета SDK для доступа к интерфейсу отладки.

## <a name="see-also"></a>См. также
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)