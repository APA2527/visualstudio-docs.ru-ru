---
title: Сбор данных параллелизма для службы с помощью средств командной строки профилировщика | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7d56f0d8540da90925ebe2f5fc4ab8f6372bc3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842449"
---
# <a name="collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Сбор данных параллелизма для службы с помощью средств командной строки профилировщика
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Метод параллелизма средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] позволяет собирать данные о конфликтах ресурсов и действиях потока, показывающие использование ЦП, конфликты потоков, миграцию потоков, задержки синхронизации, области перекрывающегося ввода-вывода и другие системные события.  
  
> [!NOTE]
> Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Приложениям для магазина Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Задача|См. также|  
|----------|---------------------|  
|**Присоединение к выполняющейся службе .NET**|-   [Как присоединить профилировщик к службе .NET для накопления данных параллелизма](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Добавление данных взаимодействия между уровнями**|-   [Сбор данных об уровневом взаимодействии](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Присоединение к выполняющейся службе C/C++**|-   [Практическое руководство. Присоединение профилировщика к собственной службе для сбора данных параллелизма](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
### <a name="profiling-windows-services"></a>Профилирование служб Windows  
  
|Задача|См. также|  
|----------|---------------------|  
|**Профилирование с помощью метода выборки**|-   [Сбор статистики приложения с использованием выборки](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Профилирование с помощью метода инструментирования**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Профилирование выделения памяти .NET и сбора мусора**|-   [Сбор данных об использовании памяти .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-concurrency-data"></a>Профилирование данных параллелизма  
  
|Задача|См. также|  
|----------|---------------------|  
|**Профилирование автономных приложений**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Профилирование веб-приложений ASP.NET**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Анализ представлений и отчетов данных параллелизма  
 [Представления данных о состязаниях за ресурсы](../profiling/resource-contention-data-views.md)  
  
 [Визуализатор параллелизма](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Справочник  
 [Справочник по Средства профилирования командной строки](../profiling/command-line-profiling-tools-reference.md)
