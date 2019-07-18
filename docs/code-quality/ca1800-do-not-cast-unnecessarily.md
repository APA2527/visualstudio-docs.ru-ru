---
title: CA1800. Не делайте лишних приведений
ms.date: 10/26/2017
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a13aeeffbc77e4f40ff886c0d890f181697fcc11
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797183"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800. Не делайте лишних приведений

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Метод выполняет повторяющиеся приведения на одном из своих аргументов или локальных переменных.

Для завершения анализа этим правилом протестированных сборки должны быть построены с помощью отладочную информацию и связанный PDB-файл должен быть доступен.

## <a name="rule-description"></a>Описание правила
Повторяющиеся приведения снижают производительность, особенно если приведения выполняются в компактных операторах итераций. Для явного приведения повторяющихся операций сохранения результата приведения в локальной переменной и используйте локальную переменную вместо дублирования операций.

Если C# `is` оператор используется для проверки ли приведение завершится успешно, прежде чем фактическое приведение будет выполнено, вам следует протестировать результат `as` оператор вместо этого. Это обеспечивает те же функциональные возможности без неявное приведение операции, выполняемой `is` оператор. Также можно использовать в C# 7.0 и более поздних версиях `is` оператор с [сопоставление шаблонов](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) преобразование типа и приведение выражения к переменной этого типа за один шаг.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените реализацию метода, чтобы свести к минимуму число операций приведения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно подавить предупреждение из этого правила, или игнорировать правило полностью, если производительность не имеет значения.

## <a name="examples"></a>Примеры
 В примере показан метод, который нарушает правило с помощью C# `is` оператор. Второй метод, соответствующий этому правилу, заменив `is` оператор на проверку результат `as` оператор, который уменьшает число операций приведения каждой итерации с двух до одной. Третий метод также выполняет правила, используя `is` с [сопоставление шаблонов](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) для создания переменной нужного типа, если преобразование типа пройдет успешно.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 В примере показан метод, `start_Click`, который имеет несколько явных приведений, который нарушает правило и метод, `reset_Click`, которой соблюдается правило, сохраняя приведения в локальной переменной.

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>См. также

- [as (Справочник по C#)](/dotnet/csharp/language-reference/keywords/as)
- [Is (Справочник по C#)](/dotnet/csharp/language-reference/keywords/is)