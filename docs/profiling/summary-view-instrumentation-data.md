---
title: Представление "Сводка" — данные инструментирования | Документы Майкрософт
description: В этой статье рассказывается, как в представлении "Сводка" отображаются сведения о создающих наибольшую нагрузку функциях, а также приводится описание ссылок на уведомления и списков отчетов.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0a9431f6f7a2adfee06f4fa007eafc109d3c32d0
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722663"
---
# <a name="summary-view---instrumentation-data"></a>Представление "Сводка" — данные инструментирования
В представлении "Сводка" приводится информация о создающих наибольшую нагрузку функциях в ходе сеанса профилирования. Дополнительные сведения, включая описание ссылок на уведомления и списков отчетов, см. в разделе [Представление "Сводка"](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Временная шкала
 Временная шкала представления "Сводка" показывает загрузку ЦП профилируемым приложением за время профилирования. Временная шкала позволяет фильтровать представление в соответствии с заданным интервалом времени. Дополнительные сведения см. в разделе [Практическое руководство. Фильтрация представлений отчетов на сводной временной шкале](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="hot-path"></a>Горячий путь
 **Горячий путь** показывает путь выполнения, потребовавший наибольшего времени. Чтобы отобразить представление сведений о функции, щелкните функцию. Для просмотра других представлений щелкните функцию правой кнопкой мыши и выберите представление из списка.

 **Горячий путь** включает следующие данные для каждой функции:

|Столбец|Описание|
|------------|-----------------|
|**Имя**|Имя функции.|
|**% затраченного инклюзивного времени**|Процент всего времени в данных профилирования, затраченного функцией на выполнение кода в теле самой функции и в вызванных ею функциях.|
|**% затраченного эксклюзивного времени**|Процент всего времени в данных профилирования, затраченного функцией на выполнение кода в теле самой функции. Не включается время выполнения функций, вызванных выбранной функцией.|

## <a name="functions-with-most-individual-work"></a>Функции с максимальной индивидуальной работой
 Список функций, потребовавших наибольшего времени на выполнение кода в теле функции, но не в вызываемых функциях.

 Раздел **Функции с максимальной индивидуальной работой** включает указанные ниже данные по каждой функции.

|Столбец|Описание|
|------------|-----------------|
|**Имя**|Имя функции.|
|**Эксклюзивное время %**|Процент всего времени в данных профилирования, затраченного функцией на выполнение кода в теле самой функции. Не включается время выполнения функций, вызванных выбранной функцией.|

## <a name="see-also"></a>См. также
- [Представление "Сводка" — данные выборки](../profiling/summary-view-sampling-data.md)
- [Представление "Сводка" — данные в памяти .NET](../profiling/summary-view-dotnet-memory-data.md)
