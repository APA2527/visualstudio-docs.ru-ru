---
title: IDiaReadExeAtRVACallback | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c86a0e995e3336bc217bcc9ad0e7ce28a6434478
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832517"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Позволяет клиентскому приложению для предоставления байт исполняемого файла, как указано по относительному виртуальному адресу.

## <a name="syntax"></a>Синтаксис

```
IDiaReadExeAtRVACallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDiaReadExeAtRVACallback`.

|Метод|Описание|
|------------|-----------------|
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Считывает указанное число байтов, начиная с указанного относительного виртуального адреса (RVA) из исполняемого файла.|

## <a name="remarks"></a>Примечания
 Клиентское приложение реализует этот интерфейс, чтобы обеспечить байты исполняемого файла с помощью относительного виртуального адреса в исполняемый файл. Чтобы использовать смещение абсолютный, реализовать [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Этот метод реализуется клиентским приложением и передается [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод как альтернативный метод для чтения файла.

## <a name="requirements"></a>Требования
 Заголовок: dia2.h

 Библиотека: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>См. также
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)