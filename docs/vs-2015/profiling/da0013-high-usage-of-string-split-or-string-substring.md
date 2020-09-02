---
title: DA0013. Интенсивное использование String.Split или String.Substring | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6ff05e7e8cc74eacb00b5ec8ff42bd48faaa12c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159194"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013. Интенсивное использование String.Split или String.Substring
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Идентификатор правила | DA0013 |  
| Категория |. Руководство по использованию NET Framework |  
| Методы профилирования | Выборка |  
| Сообщение | Рекомендуется уменьшить использование функций String. Split и String. Substring. |  
| Тип правила | Предупреждение |  
  
## <a name="cause"></a>Причина:  
 Вызовы методов System.String.Split и System.String.Substring составляют значительную часть данных профилирования. Рекомендуется использовать метод System.String.IndexOf или System.String.IndexOfAny при проверке существования подстроки в строке.  
  
## <a name="rule-description"></a>Описание правила  
 Метод Split обрабатывает объект типа "строка" и возвращает массив строк, содержащих подстроки исходной строки. Функция выделяет память для возвращаемого объекта типа "массив" и для новых объектов типа "строка" для каждого элемента массива. Аналогичным образом метод Substr обрабатывает объект типа "строка" и возвращает новую строку, эквивалентную подстроке, которая была запрошена.  
  
 Если приложение критично к управлению выделением памяти, рассмотрите возможность использования других методов вместо String.Split и String.Substr. Например, можно использовать метод IndexOf или IndexOfAny для поиска конкретной подстроки в строке символов без создания нового экземпляра класса String.  
  
## <a name="how-to-investigate-a-warning"></a>Изучение причин предупреждения  
 Дважды щелкните сообщение в окне Список ошибок, чтобы перейти к представлению [Сведения о функциях](../profiling/function-details-view.md) выборки данных профилирования. Проверьте вызовы функций, чтобы найти участки программы, в которых наиболее часто используются методы System.String.Split и System.String.Substr. По возможности старайтесь использовать методы IndexOf и IndexOfAny для поиска нужной подстроки в строке символов без создания нового экземпляра класса String.
