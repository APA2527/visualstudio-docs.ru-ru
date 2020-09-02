---
title: Практическое руководство. Фильтрация отчетов из командной строки | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db2c9d845af962fc17da1ebd84e8dd5fe6ffadab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146006"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Практическое руководство. Фильтрация отчетов из командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью параметров команды **VSPerfReport** можно фильтровать отчеты за определенный период времени в файле данных профилирования или ограничивать данные одним или несколькими процессами или потоками. Дополнительные сведения об этой команде см. в разделе [VSPerfReport](../profiling/vsperfreport.md).  
  
|Параметры|Описание|  
|-------------|-----------------|  
|**StartTime:** [*Значение*]|Отображает только данные, собранные после введенного значения (в миллисекундах).|  
|**EndTime:** [*Значение*]|Отображает только данные, собранные до введенного значения (в миллисекундах).|  
|**FilterFile:** `VSPFFile`|Задает расположение файла фильтра, созданного из окна **отчета о производительности Visual Studio**.|  
|**MsFilter:** [*Время_начала,Продолжительность*]|Отображает только данные за период `Duration` с `StartTime` (в миллисекундах).|  
|**Process:** [*Pid*]|Отображает только данные из указанного процесса.|  
|**Thread:** [*ИД_потока*]|Отображает только данные из указанного потока.|  
|**Thread:** [*ИД_потока,ИД_процесса*]|Отображает только данные из указанного потока, связанного с указанным процессом.|
