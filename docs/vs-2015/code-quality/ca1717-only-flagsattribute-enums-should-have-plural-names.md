---
title: CA1717. Только перечисления FlagsAttribute должны иметь имена во множественном числе | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: aa0c51eaa10503a92c21960dc3dd074aa7541f5c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694958"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717. Только перечисления FlagsAttribute должны иметь имена во множественном числе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя видимого перечисления заканчивается на слова во множественном числе и перечисления не помечен атрибутом <xref:System.FlagsAttribute?displayProperty=fullName> атрибута.

## <a name="rule-description"></a>Описание правила
 Соглашения об именовании диктовать, что множественное число имени перечисления указывает, что более одного значения перечисления могут быть заданы одновременно. <xref:System.FlagsAttribute> Сообщает компилятору, что перечисление должно рассматриваться как битовое поле, которое позволяет побитовых операций над перечисления.

 Если только одно значение перечисления можно указать за раз, имя перечисления должно быть словом в единственном числе. Например перечисление, определяющее дни недели, могут быть предназначены для использования в приложении, где можно указать несколько дней. Это перечисление должны иметь <xref:System.FlagsAttribute> и может быть вызвана «Дни». Похожее перечисление, которое позволяет указать только один день не атрибут и не может быть вызван «Day».

 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает время, которое требуется изучать новую библиотеку программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Формируемая перечисления словом в единственном числе, или добавьте <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из правила, если имя функции оканчивается словом в единственном числе.

## <a name="related-rules"></a>Связанные правила
 [CA1714: Перечислений флагов должны быть имена во множественном числе](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: СЛЕДУЕТ Помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также
 <xref:System.FlagsAttribute?displayProperty=fullName> [Разработка перечислений](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
