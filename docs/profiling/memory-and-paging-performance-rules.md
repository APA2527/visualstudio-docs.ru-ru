---
title: Правила производительности памяти и подкачки | Документы Майкрософт
description: Сведения о правилах производительности в категории памяти и подкачки, указывающих на действия подкачки во время профилирования, которые могут повлиять на производительность и время отклика приложения.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e1cddda12fbb67f9b604186e754146558cdd62ee
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720609"
---
# <a name="memory-and-paging-performance-rules"></a>Правила производительности памяти и подкачки
Правила производительности в категории памяти и подкачки указывают на действия подкачки во время профилирования, которые могут повлиять на производительность и время отклика приложения.

|Правило|Описание|
|-|-|
|[DA0014. Исключительно высокая скорость подкачки активной памяти на диск](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Чрезвычайно высокая интенсивность использования подкачки активной памяти на диск и с диска на протяжении сеанса профилирования. Обычно использование подкачки на таком уровне влияет на производительность и время отклика приложения. Рекомендуется сократить объем выделяемой памяти, изменив алгоритмы. Кроме того, возможно, потребуется учесть требования приложения к памяти. Попробуйте снова запустить профилирование на компьютере с большим объемом памяти. Это правило срабатывает, когда объем подкачки превышает верхнее пороговое значение правила D0017.|
|[DA0017. Высокая скорость подкачки активной памяти на диск](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Относительно высокая интенсивность использования подкачки активной памяти на диск и с диска на протяжении сеанса профилирования. Обычно использование подкачки на таком уровне влияет на производительность и время отклика приложения. Рекомендуется сократить объем выделяемой памяти, изменив алгоритмы. Кроме того, возможно, потребуется учесть требования приложения к памяти. Попробуйте снова запустить профилирование на компьютере с большим объемом памяти.|
