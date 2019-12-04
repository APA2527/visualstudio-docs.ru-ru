---
title: DA0011. Затратный метод CompareTo | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d0eb4566fd4c8a513b1492cecffc16cb94a1fd83
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779432"
---
# <a name="da0011-expensive-compareto"></a>DA0011. Затратный метод CompareTo

|||
|-|-|
|Идентификатор правила|DA0011|
|Категория|Использование .NET Framework|
|Методы профилирования|Дискретизация<br /><br /> Память .NET|
|Сообщение|Функции CompareTo должны быть малозатратными и не выделять память. Если возможно, уменьшите сложность функции CompareTo.|
|Тип правила|Предупреждение|

## <a name="cause"></a>Причина:
 Метод CompareTo типа является затратным или выделяет память.

## <a name="rule-description"></a>Описание правила
 Методы CompareTo должны быть эффективными и не выделять память.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Упростите метод CompareTo.
