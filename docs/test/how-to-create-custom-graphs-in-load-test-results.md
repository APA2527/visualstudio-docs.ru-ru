---
title: Практическое руководство. Создание пользовательских графиков в результатах нагрузочного теста
description: Сведения о том, как создать графы для отображения определенной информации о результатах нагрузочных тестов при их выполнении или после их завершения.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load test results graphs, creating
- load test results graphs
ms.assetid: 17fcafce-76f9-4411-9389-6e5376eab236
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c003fc5d6573dfdd88ec85ea37fbb10f80c94484
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441043"
---
# <a name="how-to-create-custom-graphs-in-load-test-results"></a>Практическое руководство. Создание пользовательских графиков в результатах нагрузочного теста

Можно разработать диаграммы, отображающие определенные сведения о результатах нагрузочных тестов. При создании диаграммы следует указать счетчики нагрузочных тестов, которые будут на ней представлены.

Выполнение следующих процедур осуществляется либо в ходе нагрузочного теста, либо по его завершении.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-load-test-results-graph"></a>Создание настраиваемой диаграммы результатов нагрузочного теста

1. На панели инструментов **нагрузочных тестов** нажмите кнопку **Добавить новую диаграмму**.

     \- или -

     В **анализаторе тестовой нагрузки** щелкните правой кнопкой мыши на панели **Счетчики** или в диаграмме и выберите команду **Добавить диаграмму**.

     Откроется диалоговое окно **Ввод имени диаграммы**.

2. В поле **Имя диаграммы** введите имя диаграммы и нажмите кнопку **ОК**.

     В **анализаторе тестовой нагрузки** появится новая диаграмма. Она появится в выбранной в настоящий момент области диаграммы и заменит ранее отображавшуюся диаграмму.

3. Настройте новую диаграмму, добавив в нее счетчики. Дополнительные сведения см. в разделе [Практическое руководство. добавлять и удалять счетчики на графах](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

## <a name="see-also"></a>См. также раздел

- [Анализ результатов нагрузочного тестирования в представлении диаграмм](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Практическое руководство. Добавление и удаление счетчиков на графах в результатах нагрузочного теста](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
