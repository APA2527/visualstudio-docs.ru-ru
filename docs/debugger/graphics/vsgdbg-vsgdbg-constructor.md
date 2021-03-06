---
title: VsgDbg::VsgDbg (конструктор) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 466c64f3b055eef3629f0f4666529f1be4247f42
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861339"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (конструктор)
Создает экземпляр класса `VsgDbg` с подготовкой или без подготовки компонента диагностики графики в приложении для активного захвата и записи данных графики по умолчанию, в зависимости от заданного логического параметра.

## <a name="syntax"></a>Синтаксис

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>Параметры
 `bDefaultInit` Значение `true` для указания того, что компонент диагностики графики в приложении должен быть подготовлен к активному захвату и записи данных графики; значение `false` для указания того, что в данный момент приложение не должно быть подготовлено к активному захвату и записи данных графики.

## <a name="remarks"></a>Примечания
 При вызове конструктора с параметром `bDefaultInit`, установленным в значение `true`, имя файла журнала графики зависит от того, как определены символы препроцессора `DONT_SAVE_VSGLOG_TO_TEMP` и `VSG_DEFAULT_RUN_FILENAME` до включения `vsgcapture.h` в приложение.

 При вызове конструктора с параметром `bDefaultInit`, установленным в значение `false`, компонент диагностики графики в приложении может быть подготовлен для активного захвата и записи данных графики позднее с помощью функции `Init`.

## <a name="see-also"></a>См. также
- [VsgDbg::~VsgDbg (деструктор)](vsgdbg-tilde-vsgdbg-destructor.md)
- [Init](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)