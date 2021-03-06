---
title: Счетчики ЦП и Windows | Документы Майкрософт
description: Счетчики ЦП (оборудование) и Windows (программное обеспечение) предоставляют данные о производительности. Узнайте, как просматривать их и получать от них данные.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2c3657f3558a688232424b868d0e93b8c056467c
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719166"
---
# <a name="cpu-and-windows-counters"></a>Счетчики ЦП и Windows

Профилировщик Visual Studio позволяет собирать данные о производительности, которые были сформированы операционной системой (счетчиками Windows), и данные о производительности, которые были сформированы процессором (счетчиками ЦП).

> [!NOTE]
> Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Для приложений универсальной платформы Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="windows-counters"></a>Счетчики Windows

Счетчики Windows являются компонентом инфраструктуры диагностики Windows, которая позволяет получать информацию о производительности операционной системы, приложения, службы или драйвера. Счетчики Windows определяются конфигурацией текущего компьютера, некоторые счетчики могут быть недоступны на других компьютерах. Счетчики производительности Windows собираются в файлах данных профилирования как метки профилирования, которые затем могут использоваться для фильтрования представлений и отчетов.

## <a name="cpu-counters"></a>Счетчики ЦПУ

Счетчики ЦП представляют собой функциональный механизм ЦП, который обеспечивает хранение информации о событиях, связанных с оборудованием. Когда данные счетчиков ЦП собираются с использованием метода профилирования инструментирования, данные добавляются к данным для функций и модулей. Можно собирать данные с нескольких счетчиков ЦП с помощью метода инструментирования. Если используется метод выборки, вы выбираете один счетчик, который будет использоваться как событие выборки.

Счетчики производительности зависят от конкретного ЦП. Для использования одинаковых счетчиков производительности для ЦП различных моделей или версий может потребоваться значительная настройка параметров конфигурации. Переносимые события профилировщика [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] позволяют отделить некоторые типовые счетчики производительности от конкретных моделей процессоров и позволяют собирать или осуществлять выборку общих событий производительности.

Если при использовании профилировщика необходимо выполнить подсчет количества некоторых событий, например числа промахов кэша уровня L2, можно построить сеанс анализа производительности для данного отправителя событий. Это можно сделать для любого ЦП, содержащего кэш уровня L2. Сеанс анализа производительности можно без изменений переносить с платформы на платформы.

Профилировщик Visual Studio продолжает поддерживать определенные события для конкретных платформ. Например, разработчику на платформе Pentium 4 может понадобиться выполнить подсчет событий, относящихся к архитектуре NetBurst. Такие события перенести невозможно, однако они по-прежнему доступны для определенных сеансов производительности на данной платформе.

## <a name="portable-and-platform-events"></a>Переносимые и платформенные события

Переносимые события образуют группу счетчиков ЦП, которые не зависят от определенного процессора. Все остальные счетчики ЦП называются платформозависимыми событиями; их поддержка зависит от конкретной платформы.

 И переносимые, и платформозависимые события определяются в *XML*-файлах, в которых содержатся конкретные значения, относящиеся к этим счетчикам. Таких файлов, относящихся к разным ЦП, достаточно много, так как, например, данные для ЦП Intel и AMD различаются. Профилировщик [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] использует эти сведения для предоставления пользователю оптимальных счетчиков, переносимых или платформозависимых, для измерения производительности.

### <a name="portable-events"></a>Переносимые события

В группу переносимых событий входят следующие события.

**Универсальные события**

|Имя события|Описание события|
|----------------|-----------------------|
|Завершено инструкций|Указывает количество полностью выполненных инструкций на момент создания события.|
|Не остановленные циклы|Указывает только те циклы, в которых процессор не остановлен, например ожидание ввода-вывода.|

**События внешнего интерфейса**

|Имя события|Описание события|
|----------------|-----------------------|
|Промахи ITLB|Указывает количество подстановок в аппаратном буфере ITLB (Instruction Translation Look-aside Buffer), которые закончились неудачей.|

**События ветви**

|Имя события|Описание события|
|----------------|-----------------------|
|Завершенные ветви|Указывает количество полностью выполненных инструкций в ветви на момент создания события.|
|Неверно предсказанные ветви|Указывает количество неверно предсказанных ветвей, возникших из-за того, что процессор неверно предсказал путь. Неверно предсказанные ветви приводят к снижению производительности, так как процессор должен удалить всю проделанную работу и начать сначала с правильным путем.|

**События памяти**

|Имя события|Описание события|
|----------------|-----------------------|
|Промахи чтения кэша L2|Указывает количество промахов при чтении кэша второго уровня.|
|Ссылки чтения кэша L2|Указывает количество ссылок чтения кэша второго уровня. Сюда включаются промахи при загрузке, а также промахи и попадания RFO.|

## <a name="view-available-counters"></a>Просмотр доступных счетчиков

Вы можете указать доступные счетчики ЦП в интегрированной среде разработки Visual Studio в окне командной строки.

### <a name="visual-studio-ui"></a>Пользовательский интерфейс Visual Studio

Чтобы указать доступные счетчики на компьютере в интегрированной среде разработки Visual Studio, необходимо открыть сеанс анализа производительности профилировщика в обозревателе производительности.

#### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>Просмотр списка всех счетчиков ЦП, поддерживаемых на текущей платформе

1. В обозревателе производительности щелкните правой кнопкой мыши сеанс анализа производительности, а затем выберите **Свойства**.

2. Выполните одно из следующих действий.

   - В списке события **Выборка** выберите пункты **Выборка**, **Счетчик производительности**. Счетчики ЦП отображаются в списке **Доступные счетчики производительности**.

      **Примечание.** Нажмите кнопку **Отмена**, чтобы вернуться к предыдущей конфигурации выборки.

     -или-

   - Выберите **Счетчики ЦП**, а затем — **Сбор данных счетчиков ЦП**. Счетчики ЦП отображаются в списке **Доступные счетчики**.

      **Примечание.** Нажмите кнопку **Отмена**, чтобы вернуться к предыдущей конфигурации коллекции счетчиков.

#### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>Просмотр списка счетчиков ЦП, поддерживаемых на текущей платформе

1. В обозревателе производительности щелкните правой кнопкой мыши сеанс анализа производительности, а затем выберите **Свойства**.

2. Щелкните **Счетчики Windows**.

3. Выберите **Сбор счетчиков Windows**.

4. В списке **Категория счетчика** выберите группу счетчиков. В списке отображается счетчик Windows для группы.

     **Примечание.** Нажмите кнопку **Отмена**, чтобы вернуться к предыдущей конфигурации коллекции счетчиков.

### <a name="command-line"></a>Командная строка

С помощью инструмента командной строки [VSPerfCmd](../profiling/vsperfcmd.md) можно создать список счетчиков ЦП, доступных на компьютере.

#### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>Создание списка счетчиков ЦП, поддерживаемых на текущей платформе

1. Откройте окно командной строки.

2. Type

     **\<Visual Studio Performance Tools Directory>\VSPerfCmd /querycounters**

     где *\<Visual Studio Performance Tools Directory>*  — это путь к каталогу средств оценки производительности в установке Visual Studio. Сведения о пути к средствам оценки производительности см. в статье [Указание пути к программам командной строки средств профилирования](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="see-also"></a>См. также

- [Разделы общих сведений](../profiling/overviews-performance-tools.md)
- [Практическое руководство. Выбор событий выборки](../profiling/how-to-choose-sampling-events.md)
- [Практическое руководство. Сбор данных счетчиков производительности ЦП](../profiling/how-to-collect-cpu-counter-data.md)
- [Практическое руководство. Сбор данных счетчиков производительности Windows](../profiling/how-to-collect-windows-counter-data.md)
