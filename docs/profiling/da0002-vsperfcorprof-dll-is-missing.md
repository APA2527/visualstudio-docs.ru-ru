---
title: DA0002. Отсутствует файл VSPerfCorProf.dll | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f768a35e7c50ec55867ae49901718063ca39bd0b
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777755"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002. Отсутствует файл VSPerfCorProf.dll

|||
|-|-|
|Идентификатор правила|DA0002|
|Категория|Использование средств профилирования|
|Методы профилирования|Профилирование с помощью программ командной строки VSPerfCmd и VSPerfASPNETCmd|
|Сообщение|По-видимому, сбор данных для файла был выполнен без должной настройки переменных среды с помощью *VSPerfCLREnv.cmd*. Разрешение символов для управляемых двоичных данных может быть невозможно.|
|Тип правила|Сведения|

## <a name="cause"></a>Причина:
 Профилировщику не удалось найти библиотеку *VSPerfCorProf.dll* во время сеанса профилирования. Это предупреждение выводится, если программы командной строки для сбора данных профилирования используются без применения программы *VSPerfCLREnv.cmd* для инициализации необходимых переменных среды. Это предупреждение также может выдаваться, если при запуске Средств профилирования выполняется другой профилировщик.

## <a name="rule-description"></a>Описание правила
 Перед выполнением профилирования необходимо задать определенные переменные среды, чтобы профилировщик мог разрешить символы в двоичные файлы .NET Framework. Это предупреждение указывает на то, что перед сбором данных профилирования не запускалось средство *VSPerfCLREnv.cmd*. Разрешение символов для управляемых двоичных данных может быть невозможно. Дополнительные сведения об использовании Средств профилирования из командной строки см. в разделе [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Когда вы профилируете управляемые приложения с помощью программ командной строки в Средствах профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], запустите программу командной строки [VSPerfCLREnv](../profiling/vsperfclrenv.md), прежде чем начинать сбор данных.
