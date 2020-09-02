---
title: Функция Сккжетверсион | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a563a7d1d65dc4c6564abd4e337242eea1aa9924
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700677"
---
# <a name="sccgetversion-function"></a>Функция SccGetVersion
Эта функция возвращает номер версии API подключаемого модуля системы управления версиями, поддерживаемый подключаемым модулем системы управления версиями.

## <a name="syntax"></a>Синтаксис

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Параметры
 Нет.

## <a name="return-value"></a>Возвращаемое значение
 `LONG`Тип данных, содержащий номер версии поддерживаемого интерфейса API подключаемого модуля системы управления версиями:

|WORD|Описание|
|----------|-----------------|
|HIWORD|Основной номер версии|
|ловорд|Дополнительный номер версии|

## <a name="remarks"></a>Remarks
 Например, если подключаемый модуль системы управления версиями поддерживает версию 1,3 API подключаемого модуля системы управления версиями, эта функция возвратит 0x0103.

## <a name="see-also"></a>См. также раздел
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
