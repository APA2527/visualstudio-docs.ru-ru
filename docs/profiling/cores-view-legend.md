---
title: Легенда представления "Ядра" | Документы Майкрософт
description: Сведения о легенде представления "Ядра", в которой в табличном виде представлены данные по переключению контекста и выбору потоков. Также в этой статье приводятся сведения о переключениях контекста и производительности.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.legend
helpviewer_keywords:
- Concurrency Visualizer, Cores View Legend
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e4486bc20caf580c9a2c1038002693bd92fe616a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882925"
---
# <a name="cores-view-legend"></a>Легенда представления "Ядра"
В легенде представления "Ядра" каждый поток обозначается с помощью цвета и имени. Она включает в себя столбцы, которые показывают количество переключений контекста между ядрами и процент переключений контекста между ядрами. Строки в легенде сортируются по количеству переключений контекста между ядрами по убыванию.

 Допускается выбор строк в условных обозначениях для фильтрации потоков, которые отображаются на временной шкале. На временной шкале отображаются только выбранные потоки. Если строки не выбраны, на временной шкале будут отображены все строки.

 Переключения контекста между ядрами требуют больше накладных расходов и расходов ресурсов, чем переключения, остающиеся на том же логическом ядре. Во время переключений контекста сохраняются и восстанавливаются регистры процессора и код ядра операционной системы, перезагружается ассоциативный буфер трансляции инструкций и очищается конвейер процессора. Переключения контекста между ядрами могут быть еще более дорогими по сравнению с другими переключениями контекста, так как данные кэша являются недопустимыми для этого потока на другом ядре. Напротив, если поток переключился на ядро, на котором он перед этим выполнялся, то, вероятно, полезные данные все еще находятся в кэше. Если при увеличении количества межъядерных переключений контекста было увеличено количество попыток управления сходством потоков и произошло ухудшение производительности, необходимо решить, можно ли устранить эту проблему. Необходимо начать с устранения сходства потоков, после чего посмотреть полученное межъядерное поведение.

 Элементы легенды описаны в следующей таблице.

|Элемент|Определение|
|-------------|----------------|
|Имя потока|Цвет потока во временной шкале предыдущих ядер выше и имя данного потока.|
|Переключений контекста между ядрами|Количество переключений контекста для потока, который также переключается с одного логического ядра на другое. Не существует различий между переключениями контекста между ядрами, которые осуществляются на разных ядрах процессора, и теми, которые остаются на том же.|
|Всего переключений контекста|Общее количество переключений контекста для данного потока во время выборки. При каждом изменении контекста потока (например, с выполнения на синхронизацию) учитывается одно переключение контекста.|
|Процент переключений контекста между ядрами|Рассчитывается как процент путем деления количества переключений контекста на количество всех переключений контекста. Чем выше этот процент, тем больше общее влияние служебных данных переключений контекста между ядрами на производительность данного потока.|

## <a name="see-also"></a>См. также раздел
- [Представление "Ядра"](../profiling/cores-view.md)