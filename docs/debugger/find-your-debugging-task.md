---
title: Часто задаваемые вопросы. Поиск функции отладки
description: Часто задаваемые вопросы, которые помогут вам определить функцию отладчика, которая поможет отладить приложение
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c215b232c64b97c57285618056ee4675587b48e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870718"
---
# <a name="faq---find-the-debugging-feature-you-need-in-visual-studio"></a>Часто задаваемые вопросы. Поиск нужной функции отладки в Visual Studio

Если вам нужна помощь по сопоставлению задачи отладки с соответствующей функцией отладчика Visual Studio, используйте ссылки из этой статьи. Приведенный здесь список задач содержит типичные задачи, такие как приостановка кода для отладки, проверка переменных и отправка сообщений в окно **вывода**. Если вам нужны общие сведения о функциях отладчика, обратитесь к разделу [Первое знакомство с отладчиком](debugger-feature-tour.md).

## <a name="fix-an-exception"></a>Исправление исключения

- См. раздел [Исправление исключения](write-better-code-with-visual-studio.md#fix-an-exception).

## <a name="pause-running-code"></a>Приостановка выполнения кода

- **Приостановка выполнения кода для проверки строки кода, которая может содержать ошибку**

  Задайте точку останова. Для получения дополнительной информации см. раздел [Использование точек останова](using-breakpoints.md).

- **Приостановка и проверка приложения при достижении определенного состояния**

  Используйте условную точку останова, чтобы управлять тем, где и когда точка останова активируется, с помощью условной логики. Дополнительные сведения см. в разделе [Условия точек останова](using-breakpoints.md#breakpoint-conditions).

- **Приостановка кода только при изменении значения или свойства конкретного объекта**

  Для C++ задайте [точку останова в данных](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
  ::: moniker range=">= vs-2019"
  Для приложений, использующих .NET Core 3, можно также задать [точку останова в данных](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
  ::: moniker-end

  В противном случае, только для C# и F#, можно [отслеживать идентификатор объекта с помощью условной точки останова](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

- **Приостановка кода внутри цикла на определенной итерации**

  Задайте точку останова, используя **количество обращений** в качестве условия. Дополнительные сведения см. в разделе [Количество обращений](using-breakpoints.md#set-a-hit-count-condition).

- **Приостановка кода в начале функции, когда известно имя функции, но не ее расположение**

  Это можно сделать с помощью точки останова в функции. Дополнительные сведения см. в разделе [Задание точек останова в функции](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Приостановка кода в начале нескольких функций с одинаковым именем**

  При наличии нескольких функций с одинаковыми именами (перегруженные функции или функции в разных проектах) можно использовать [точку останова в функции](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Управление точками останова и их отслеживание**

  Используйте окно **Точки останова**. Дополнительные сведения см. в разделе [Управление точками останова](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

- **Приостановка кода и отладка при возникновении определенного обработанного или необработанного исключения**

  Хотя помощник по исправлению ошибок показывает, где произошла ошибка, если вы хотите приостановить выполнение и отладить конкретную ошибку, можно [велеть отладчику прервать выполнение при возникновении исключения](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

- **Задание точки останова из стека вызовов**

  Если вы хотите приостановить и отладить код при проверке потока выполнения или просмотре функций в окнах **стека вызовов**, см. раздел [Задание точки останова в окне стека вызовов](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

- **Приостановка кода в указанной инструкции сборки**

  Это можно сделать, [задав точку останова в окне дизассемблирования](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Выполнение кода

- **Использование команд для пошагового выполнения кода во время отладки**

  Дополнительные сведения см. в разделе [Навигация по коду с помощью отладчика](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Проверка данных

- **Проверка значений переменных во время выполнения приложения**

  Наведите указатель мыши на переменные, используя [подсказки по данным](view-data-values-in-data-tips-in-the-code-editor.md), или [проверьте переменные в окне видимых и локальных переменных](autos-and-locals-windows.md).

- **Наблюдение за изменением значения конкретной переменной**

  Установите контрольное значение для переменной. Дополнительные сведения см. в разделе [Установка контрольных значений для переменных](watch-and-quickwatch-windows.md).

- **Просмотр слишком длинных строк для окна отладчика**

  Откройте встроенный [визуализатор строк](view-strings-visualizer.md) во время отладки.

## <a name="debug-an-app-that-is-already-running"></a>Отладка уже запущенного приложения

- См. раздел [Присоединение к выполняемому процессу](attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="debug-multithreaded-applications"></a>Отладка многопоточных приложений

- См. раздел [Отладка многопоточных приложений](debug-multithreaded-applications-in-visual-studio.md).

## <a name="configure-debugging"></a>Настройка отладки

- **Настройка параметров отладчика**

  Сведения о настройке параметров отладчика и параметров проекта отладчика см. в разделе [Параметры отладчика и подготовка](debugger-settings-and-preparation.md).

- **Настройка сведений, отображаемых в отладчике**

  Вам может потребоваться отобразить сведения, отличные от типа объекта, в качестве значения в различных окнах отладчика. Для кода C#, Visual Basic, F#, и C++/CLI используйте атрибут [DebuggerDisplay](using-the-debuggerdisplay-attribute.md). Для более сложных вариантов можно также настроить пользовательский интерфейс, создав [пользовательский визуализатор](create-custom-visualizers-of-data.md).

  Для машинного кода C++ используйте [платформу NatVis](create-custom-views-of-native-objects.md).

## <a name="additional-tasks"></a>Дополнительные задачи

- **Изменение кода во время сеанса отладки**

  Используйте функцию [Изменить и продолжить](edit-and-continue.md). Для XAML используйте [Горячую перезагрузку XAML](../xaml-tools/xaml-hot-reload.md).

- **Отправка сообщений в окно вывода без изменения кода**

  Задайте точку трассировки. Дополнительные сведения см. в разделе [Использование точек трассировки](using-tracepoints.md).

- **Просмотр порядка, в котором вызываются функции**

  См. раздел [Просмотр стека вызовов](how-to-use-the-call-stack-window.md).

- **Отладка на удаленных компьютерах**

  См. раздел [Удаленная отладка](remote-debugging.md).

- **Исправление проблем производительности**

  См. раздел [Первое знакомство со средствами профилирования](../profiling/profiling-feature-tour.md).
