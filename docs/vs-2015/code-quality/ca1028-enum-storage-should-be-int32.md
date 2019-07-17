---
title: CA1028. Хранилище перечислений должно иметь тип Int32 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e79eb7e0ed33184103cc772c13515959cf973ecc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192812"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028. Хранилище перечисляемых типов должно относиться к типу Int32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Базовый тип открытого перечисления не является <xref:System.Int32?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Перечисление является типом значения, которое определяет набор связанных именованных констант. По умолчанию <xref:System.Int32?displayProperty=fullName> для хранения значения константы используется тип данных. Несмотря на то, что вы можете изменить это базовый тип, не требуется или не рекомендуется для большинства сценариев. Обратите внимание, что не прирост производительности обеспечивается использованием типом данных, меньше, чем <xref:System.Int32>. Если нельзя использовать тип данных по умолчанию, следует использовать один из распространенных системы языков программирования (CLS)-совместимые целочисленных типов, <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, или <xref:System.Int64> чтобы убедиться в том, что все значения перечисления могут быть отображены в CLS-совместимым языков программирования.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, если имеются проблемы с размером и совместимостью, используйте <xref:System.Int32>. Для ситуаций, где <xref:System.Int32> недостаточно велик для хранения значений, используйте <xref:System.Int64>. Если требуется более короткого типа данных обратной совместимости с помощью <xref:System.Byte> или <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, только в том случае, если это требуется для проблемах обратной совместимости. В приложениях сбой в соответствии с этим правилом, обычно не вызывает проблем. В библиотеках, где необходима взаимодействие языков, Несоблюдение этого правила может неблагоприятно повлиять на пользователей.

## <a name="example-of-a-violation"></a>Пример нарушения

### <a name="description"></a>Описание
 В следующем примере показано два перечисления, которые следует использовать рекомендованный базовый тип данных.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>Пример того, как для исправления

### <a name="description"></a>Описание
 В следующем примере устраняется нарушение устраняется путем изменения базового типа данных для <xref:System.Int32>.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1008: Перечисления должны иметь нулевое значение](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: СЛЕДУЕТ Помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Не значения перечислений именем «Reserved»](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Не добавляйте префикс в виде значения перечисления с именем типа](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>См. также
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>
