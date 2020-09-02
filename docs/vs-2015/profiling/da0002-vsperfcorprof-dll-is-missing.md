---
title: 'DA0002: отсутствует файл VSPerfCorProf.dll | Документы Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5723506415a0ddbf816b896e23e93eaa706bf7e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158729"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002. Отсутствует файл VSPerfCorProf.dll
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Идентификатор правила | DA0002 |  
| Категория | Использование Средства профилирования |  
| Методы профилирования | Профилирование с помощью средств командной строки VSPerfCmd и VSPerfASPNETCmd |  
| Сообщение | Возможно, файл был собран без правильной настройки переменных среды с помощью VSPerfCLREnv. cmd. Разрешение символов для управляемых двоичных данных может быть невозможно.|  
| Тип правила | Сведения |  
  
## <a name="cause"></a>Причина  
 Профилировщику не удалось найти библиотеку VSPerfCorProf.dll во время сеанса профилирования. Это предупреждение выводится, если программы командной строки для сбора данных профилирования используются без применения программы VSPerfCLREnv.cmd для инициализации необходимых переменных среды. Это предупреждение также может выдаваться, если при запуске Средств профилирования выполняется другой профилировщик.  
  
## <a name="rule-description"></a>Описание правила  
 Перед выполнением профилирования необходимо задать определенные переменные среды, чтобы профилировщик мог разрешить символы в двоичные файлы .NET Framework. Это предупреждение указывает на то, что перед сбором данных профилирования не запускалось средство VSPerfCLREnv.cmd. Разрешение символов для управляемых двоичных данных может быть невозможно. Дополнительные сведения об использовании Средства профилирования из командной строки см. в разделе [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md) .  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Когда вы профилируете управляемые приложения с помощью программ командной строки в Средствах профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], запустите программу командной строки [VSPerfCLREnv](../profiling/vsperfclrenv.md), прежде чем начинать сбор данных.
