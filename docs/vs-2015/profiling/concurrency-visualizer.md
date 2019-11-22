---
title: Визуализатор параллелизма | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c407475f72684360551cd97852c1a1bfde5088f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300613"
---
# <a name="concurrency-visualizer"></a>Визуализатор параллелизма
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ПРИМЕЧАНИЕ
> Визуализатор параллелизма — это дополнительное расширение Visual Studio. Загрузите визуализатор параллелизма и средства сбора данных визуализатора параллелизма по следующим ссылкам:  
> 
> - Скачать расширение              [Визуализатор параллелизма](https://visualstudiogallery.msdn.microsoft.com/a6c24ce9-beec-4545-9261-293061436ee9) .  
>   - Скачайте              [средства сбора данных визуализатора параллелизма для Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103).  
> 
>   С помощью [служебной программы командной строки "Визуализатор параллелизма" (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) можно собирать трассировки из командной строки, чтобы просматривать их в визуализаторе параллелизма для Visual Studio 2015. Это средство можно использовать на компьютерах без установленной среды Visual Studio.  
  
 Визуализатор параллелизма можно использовать для изучения работы многопоточного приложения. Представления в визуализаторе параллелизма предоставляют графические, табличные и текстовые данные, отражающие временные связи между потоками в программе и системе в целом. С помощью визуализатора параллелизма можно найти узкие места по производительности, случаи избыточного использования ЦП, конфликты потоков, межъядерную миграцию потоков, задержки синхронизации, действия DirectX, области перекрывающихся операций ввода-вывода и другие сведения. Эти представления предоставляют данные, действия с которыми можно выполнять путем связывания выводимой графической информации со стеками вызова и исходным кодом.  
  
 Визуализатор параллелизма основывается на функции [Трассировка событий Windows](https://go.microsoft.com/fwlink/?LinkId=234579) .  
  
> [!NOTE]
> Визуализатор параллелизма не поддерживает веб-проекты.  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Представление "Использование"](../profiling/utilization-view.md)|Содержит описание процедуры просмотра и анализа системных действий для всех процессоров.|  
|[Представление потоков](../profiling/threads-view-parallel-performance.md)|Содержит описание процедуры анализа взаимодействия между потоками программы.|  
|[Представление "Ядра"](../profiling/cores-view.md)|Содержит описание процедуры анализа миграции потоков между ядрами.|  
|[Общие шаблоны для неправильно работающих многопоточных приложений](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Описывает несколько общих шаблонов и показывает, как они отображаются в визуализаторе параллелизма.|  
|[Блог о параллельной разработке в Visual Studio](https://go.microsoft.com/fwlink/?LinkId=235385)|Содержит советы и рекомендации для визуализатора параллелизма.|  
|[Представления отчетов о производительности](../profiling/performance-report-views.md)|Содержит справочные сведения по отчетам и представлениям средств профилирования Visual Studio.|  
|[Пакет SDK визуализатора параллелизма](../profiling/concurrency-visualizer-sdk.md)|Описывает, как инструментировать исходный код для отображения дополнительных сведений в визуализаторе параллелизма.|  
|[Служебная программа командной строки "Визуализатор параллелизма" (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Описывает, как использовать программу командной строки визуализатора параллелизма (CVCollectionCmd.exe) для сбора и обработки трассировки на компьютерах, на которых не установлена Visual Studio.|  
  
## <a name="see-also"></a>См. также раздел  
 [Средства профилирования](../profiling/profiling-tools.md)
