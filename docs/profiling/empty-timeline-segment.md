---
title: Пустой сегмент временной шкалы | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a96cdc7ae4edc7ea7193d5b95dfc73fa1747c1fb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970113"
---
# <a name="empty-timeline-segment"></a>Пустой сегмент временной шкалы
В визуализаторе параллелизма причина, по которой часть временной шкалы пуста (имеет белый фон), зависит от типа канала.

- Для канала потока ЦП это означает, что поток не существовал на этом промежутке временной шкалы. Если вы заинтересованы в потоке, можно найти соответствующий промежуток выполнения, используя элементы управления масштабирования или прокрутки по горизонтали.

- Для канала ввода-вывода это означает, что в данный момент времени не выполнялся доступ к диску от имени целевого процесса.

- Для канала DirectX это означает, что никакая работа графического процессора не выполнялась от имени целевого процесса в этом промежутке временной шкалы.

- Для канала маркеров это означает, что маркеры не создавались.

## <a name="see-also"></a>См. также раздел
- [Представление "Потоки"](../profiling/threads-view-parallel-performance.md)
- [Элемент управления масштабом (представление "Потоки")](../profiling/zoom-control-threads-view.md)