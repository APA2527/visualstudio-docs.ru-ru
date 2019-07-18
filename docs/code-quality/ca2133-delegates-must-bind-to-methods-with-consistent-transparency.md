---
title: CA2133. Делегаты должны быть привязаны к методам с соответствующей прозрачностью
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0745506bfe55305c9c3a55f57823e5d80c453006
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796742"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133. Делегаты должны быть привязаны к методам с соответствующей прозрачностью

|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

> [!NOTE]
> Это предупреждение применяется только к коду, на котором работает CoreCLR (версия среды CLR, предназначенную для веб-приложения Silverlight).

## <a name="cause"></a>Причина

Это предупреждение вызывается методом, который привязывает делегат, помеченный с <xref:System.Security.SecurityCriticalAttribute> в метод, который является прозрачным или помечен с помощью <xref:System.Security.SecuritySafeCriticalAttribute>. Предупреждение также запускает метод, который привязывает прозрачный или безопасный делегат к критическому методу.

## <a name="rule-description"></a>Описание правила

Типы делегатов и методы, которые они привязаны к должны иметь согласованную прозрачность. Прозрачные и надежными с точки зрения делегаты только может привязываться к другой прозрачный или безопасный методы. Аналогичным образом критические делегатов может только привязать критические методы. Эти правила привязки убедитесь, что единственным кодом, который можно вызвать метод через делегат также может вызвать тот же метод напрямую. Например правила привязки запретить прозрачный код вызова кода critical непосредственно через прозрачный делегат.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого предупреждения, измените прозрачность делегата или метода, который привязывает таким образом, чтобы прозрачность двух эквивалентны.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

### <a name="code"></a>Код

[!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]