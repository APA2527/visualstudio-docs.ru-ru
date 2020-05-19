---
title: CaptureCurrentFrame | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9967d776845088e707035c7b1c56855ac80af82
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736137"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Захватывает оставшуюся часть текущего кадра в файл журнала графики.

## <a name="syntax"></a>Синтаксис

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Примечания
 Если в данный момент выполняется другой захват — например, запущенный функцией `BeginCapture` — тот захват завершается и записывается в журнал графики как отдельный кадр. Сразу же после этого диагностика графики начинает захват остатка текущего кадра, который также записывается как отдельный кадр. Окончание текущего кадра отмечено вызовом метода Present.

 Для захвата кадра необходимо подготовить приложение к захвату и записи данных графики, т. е. необходимо вызвать метод [Init](init.md) посредством экземпляра класса `VsgDbg`, прежде чем вызывать `CaptureCurrentFrame`.

## <a name="see-also"></a>См. также
- [Init](init.md)
- [BeginCapture](begincapture.md)