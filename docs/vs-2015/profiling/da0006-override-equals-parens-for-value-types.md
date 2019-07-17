---
title: DA0006. Переопределение Equals() для типов значений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2229edad7ff338251fea23740343e23f87aa2792
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158669"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006. Переопределение Equals() для типов значений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ИД правила | DA0006 |  
| Категория |. Использование .NET Framework |  
| Методы профилирования | Выборка |  
| Сообщение | Переопределения Equals и оператор равенства для типов значений. |  
| Тип сообщения | Предупреждение |  
  
## <a name="cause"></a>Причина  
 Вызовы метода Equals или операторов равенства открытого типа составляют значительную часть данных профилирования. Рекомендуется использовать более эффективный метод.  
  
## <a name="rule-description"></a>Описание правила  
 В унаследованной реализации Equals для типов значений используется библиотека <xref:System.Reflection> и сравнивается содержимое всех полей типа. Отражение является процессом, требующим с точки зрения вычислений больших затрат, и сравнение каждого поля на равенство может быть лишним. Если предполагается, что пользователи будут сравнивать, сортировать экземпляры или использовать их в качестве ключей хэш-таблиц, тип значения должен реализовывать Equals. Если язык программирования поддерживает перегрузку операторов, также необходимо предоставить реализацию операторов равенства и неравенства.  
  
 Дополнительные сведения о переопределении Equals и операторов равенства см. в разделе [Правила реализации метода Equals и оператора равенства (==)](http://go.microsoft.com/fwlink/?LinkId=177818).  
  
## <a name="how-to-investigate-a-warning"></a>Изучение причин предупреждения  
 Пример реализации Equals и операторов равенства см. в описании правила анализа кода [CA1815: Переопределяйте операторы Equals и равенства для типов значений](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)
