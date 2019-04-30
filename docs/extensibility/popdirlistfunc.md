---
title: POPDIRLISTFUNC | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 259ada240d81b87d2d36e12cddcc28efe8d893f1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806100"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Это функция обратного вызова, присвоенный [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) функции, чтобы обновить коллекцию каталогов и (необязательно) имена файлов, чтобы узнать, которые являются в системе управления версиями.

 `POPDIRLISTFUNC` Обратного вызова должен вызываться только для этих имен файлов и папок (в списке, присвоенный `SccPopulateDirList` функции), которые фактически в системе управления версиями.

## <a name="signature"></a>Подпись

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Параметры
 pvCallerData

[in] Значение пользователя, присвоенный [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bFolder

[in] `TRUE` Если имя в `lpDirectoryOrFileName` является каталогом; в противном случае имя является именем файла.

 lpDirectoryOrFileName

[in] Полный локальный путь к имени файла или каталога, в системе управления версиями.

## <a name="return-value"></a>Возвращаемое значение
 Интегрированная среда разработки возвращает код соответствующее сообщение об ошибке:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Продолжайте обработку.|
|SCC_I_OPERATIONCANCELED|Остановите обработку.|
|SCC_E_xxx|Любая ошибка соответствующего исходного элемента управления следует остановить обработку.|

## <a name="remarks"></a>Примечания
 Если `fOptions` параметр `SccPopulateDirList` функция содержит `SCC_PDL_INCLUDEFILES` флаг, то список будет содержать имена файлов, а также имена каталогов.

## <a name="see-also"></a>См. также
- [Функции обратного вызова, реализованные интегрированной среды разработки](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Коды ошибок](../extensibility/error-codes.md)