---
title: Сбор данных счетчиков производительности Windows | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 79ab9869f71fa8630b070c03d21ea4f9a6113622
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852645"
---
# <a name="how-to-collect-windows-counter-data"></a>Практическое руководство. Сбор данных счетчиков производительности Windows

Счетчики Windows являются счетчиками производительности системы. Сбор данных с них можно выполнять через заданные интервалы во время профилирования. В представлении "Метки" отчета средств профилирования строка имеет метку **AutoMark** для каждого интервала сбора данных. Строка содержит столбцы, которые описывают значения счетчиков производительности в этом интервале. Чтобы ограничить период анализа интервалом между двумя определенными метками, выберите метки, щелкните их правой кнопкой мыши и выберите в контекстном меню команду **Фильтрация по** > **Метки**.

> [!NOTE]
> Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Для приложений универсальной платформы Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-collect-windows-counter-data"></a>Сбор данных счетчиков производительности Windows

1. В обозревателе производительности щелкните правой кнопкой мыши сеанс, для которого требуется настроить счетчики Windows, и выберите **Свойства**.

2. В окне **Страницы свойств** щелкните страницу **Счетчики Windows**.

3. Установите флажок **Сбор счетчиков Windows**.

4. В текстовом поле **Интервал сбора (мс)** введите интервал времени.

5. Выберите категорию в раскрывающемся списке **Категория счетчика**.

6. Выберите экземпляр в раскрывающемся списке **Экземпляр**.

7. Выберите счетчики, которые будут использоваться при профилировании приложения.

8. Нажмите кнопку **Применить**.

## <a name="see-also"></a>См. также

[Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)
[Свойства сеанса анализа производительности](../profiling/performance-session-properties.md)
[Счетчики ЦП и Windows](../profiling/cpu-and-windows-counters.md)
