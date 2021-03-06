---
title: Приступая к работе со средствами оценки производительности | Документы Майкрософт
description: Сведения о нескольких способах сбора, просмотра и анализа данных производительности кода в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2018
ms.topic: conceptual
helpviewer_keywords:
- getting started, performance
- getting started, profiling tools
ms.assetid: 02085214-a8e4-40fd-9b26-32391a7a7082
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1eb65e3cb8273f36cd9255bc0a3a2f8e91689f39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907372"
---
# <a name="getting-started-with-performance-tools"></a>Приступая к работе со средствами оценки производительности

Visual Studio предоставляет несколько способов для сбора, просмотра и анализа данных производительности кода. Во многих случаях для начала работы со средствами оценки производительности лучше всего использовать параметры по умолчанию в **мастере производительности**. Мастер собирает статистические данные приложения, позволяющие выявить проблемы с производительностью в коде.

- Предупреждения о производительности, уведомляющие о распространенных проблемах кода, отображаются в окне **Список ошибок** Visual Studio. Вы можете переходить от предупреждений к исходному коду и подробным разделам справки, которые помогут написать более эффективный код.

- Отчеты о производительности позволяют изучить разные уровни структуры приложения, строки исходного кода и процессы. Отчеты о производительности показывают данные о выполнении приложения — от вызывающих и вызываемых функций определенной функции до дерева вызовов всего приложения.

Чтобы быстро профилировать проект, приложение или веб-сайт ASP.NET, выберите **Отладка** > **Профилировщик производительности** и затем **Мастер производительности**. Подробные инструкции см. в разделах [Руководство по профилированию производительности для начинающих](../profiling/beginners-guide-to-cpu-sampling.md) и [Практическое руководство. Сбор данных производительности для веб-сайта](../profiling/how-to-collect-performance-data-for-a-web-site.md).

Чтобы вручную указать и настроить сеанс профилирования производительности, выберите **Отладка** > **Профилировщик** > **Обозреватель производительности**. Используйте папку **Целевые объекты** и страницы **Свойства** в **обозревателе производительности**, чтобы настроить сеансы. Инструкции см. в разделе [Практическое руководство. Создание сеансов анализа производительности вручную](../profiling/how-to-manually-create-performance-sessions.md).

**См. также:**

- [Обзоры средств оценки производительности](../profiling/overviews-performance-tools.md)
- [Анализ данных средств оценки производительности](../profiling/analyzing-performance-tools-data.md)
- [Использование правил производительности для анализа данных](../profiling/using-performance-rules-to-analyze-data.md)
- [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)
