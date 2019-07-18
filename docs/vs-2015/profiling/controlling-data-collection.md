---
title: Управление сбором данных | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e34c4db965cacefabe752774e393a4339042040e
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54780951"
---
# <a name="controlling-data-collection"></a>Управление сбором данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Средства профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] позволяют управлять сбором данных в ходе сеанса анализа производительности и задавать профилируемые функции. В этом разделе описывается запуск и останов сбора данных с помощью окон **Обозреватель производительности** и **Управление сбором данных**, а также выбор объектов, для которых выполняется сбор данных профилирования.  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Запуск и остановка профилирования.** Вы можете начать профилирование приложения, когда запускается приложение, или можно подключить профилировщик к уже выполняемому процессу. Во время выполнения целевого приложения сбор данных можно приостанавливать и возобновлять. Чтобы закончить сеанс профилирования, закройте целевое приложение или отключите профилировщик от выполняемого процесса.|-   [Практическое руководство. Начало и окончание сбора данных о производительности](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Практическое руководство. Присоединение средств производительности к выполняющемуся процессу и его отсоединение от этого процесса](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Практическое руководство. Приостановка и возобновление сбора данных о производительности](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**Настройка профилирования инструментирования для ограничения собранных данных.** Вы можете использовать свойства конфигурации сеанса анализа производительности, чтобы ограничить данные, собранные в ходе запусков профилирования, которые используют метод инструментирования. Можно включать или исключать определенные DLL-файлы, пространства имен, классы и функции. Кроме того, можно исключать функции, которые не соответствуют заданному пороговому размеру.|-   [Практическое руководство. Ограничение инструментирования указанными библиотеками DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Практическое руководство. Ограничение инструментирования указанными функциями](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Практическое руководство. Исключение и включение малых функций при инструментировании](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## <a name="related-sections"></a>Связанные разделы  
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>См. также раздел  
 [Обозреватель производительности](../profiling/performance-explorer.md)
