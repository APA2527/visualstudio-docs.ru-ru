---
title: Профилирование автономных приложений из командной строки | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f4b2b78f7187b7a49b78312a1105a2af884fda3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186642"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Профилирование автономных приложений из командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе описываются процедуры и параметры сбора данных о производительности для автономных (клиентских) приложений с помощью средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] из командной строки.  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Задача|Связанная информация|  
|----------|---------------------|  
|**Сбор статистики приложения.** Использование метода выборки для сбора статистики производительности. Данные выборки служат для анализа проблем использования ЦП и для изучения общих характеристик производительности приложения.|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Сбор подробных сведений о времени.** Использование метода инструментирования для сбора подробных сведений о времени. Данные инструментирования удобно использовать для анализа ошибок ввода-вывода и подробного анализа сценариев приложений.|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Сбор данных об использовании памяти .NET.** Использование выборки или инструментирования для сбора данных о выделения памяти .NET, содержащих размер и количество объектов, для которых выделена память. Кроме того, можно собирать данные о времени существования объектов, в которых указывается размер и количество объектов, собранных в каждом поколении сборки мусора.|-   [Сбор данных об использовании памяти .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Сбор данных о параллелизме.** Использование метода параллелизма для сбора данных о конфликтах ресурсов и действиях потока, позволяющих определить использование ЦП, конфликты потоков, миграцию потоков, задержки синхронизации, области перекрывающегося ввода-вывода и другие системные события.|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Добавление данных взаимодействия между уровнями.** Можно добавлять данные производительности о синхронных вызовах ADO.NET, выполняемых приложением к базе данных Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Добавление данных об уровневом взаимодействии в сеанс профилирования требует определенных процедур со средствами профилирования командной строки.|-   [Сбор данных взаимодействия уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Экспериментальная проверка.** Использование пошаговых процедур для профилирования примера клиентского приложения с помощью метода выборки или инструментирования.|-   [Пошаговое руководство: Профилирование из командной строки с помощью выборки](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Пошаговое руководство: Профилирование из командной строки с помощью метода инструментирования](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Профилирование приложений ASP.NET**|-   [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**Профилирование служб**|-   [Профилирование служб](../profiling/command-line-profiling-of-services.md)|
