---
title: Практическое руководство. Определение среды выполнения .NET Framework | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f631e8639c1004fa2cb005da3b6c8bcb27f1a9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203411"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Практическое руководство. Определение среды выполнения .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В выпуске [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] можно составлять приложения из модулей, построенных с помощью разных версий среды выполнения [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. По умолчанию средства профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] профилируют первую среду выполнения, загруженную приложением. Можно указать среду выполнения для профилирования при запуске приложения с помощью профилировщика и при подключении профилировщика к уже запущенному приложению.  
  
 **Требования**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Указание профилируемой среды выполнения .NET Framework при запуске приложения с помощью профилировщика  
  
1. В **обозревателе производительности** щелкните правой кнопкой мыши сеанс анализа производительности, выберите пункт **Свойства**, а затем **Дополнительно**.  
  
     В списке **Целевая версия CLR** отображается **Автоматически** и версия среды выполнения [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], которая установлена на компьютере.  
  
2. Выполните одно из следующих действий.  
  
    - Выберите версию среды CLR для профилирования.  
  
    - Щелкните пункт **Автоматически**, чтобы выполнить профилирование первой версии, загруженной приложением.  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Указание профилируемой среды выполнения .NET Framework при подключении профилировщика к приложению  
  
1. В меню "Анализ" наведите указатель мыши на пункт "Профилировщик" и щелкните "Присоединить/отсоединить".  
  
2. В диалоговом окне "Присоединить профилировщик к процессу" щелкните процесс, который необходимо профилировать.  
  
     В списке **Целевая версия CLR** отображается **Автоматически** и версии среды выполнения [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], установленные на компьютере.  
  
3. Выполните одно из следующих действий.  
  
    - Выберите версию среды CLR для профилирования.  
  
    - Щелкните **Автоматически** для профилирования версии, загружаемой при подключении профилировщика к приложению.
