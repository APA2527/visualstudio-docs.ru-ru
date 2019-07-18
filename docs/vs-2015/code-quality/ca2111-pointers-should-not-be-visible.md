---
title: CA2111. Указатели не должны быть видимыми | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8497433088e4c49868a76dd3281d02a5e79babe5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154364"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111. Указатели не должны быть видимыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный <xref:System.IntPtr?displayProperty=fullName> или <xref:System.UIntPtr?displayProperty=fullName> поле не только для чтения.

## <a name="rule-description"></a>Описание правила
 <xref:System.IntPtr> и <xref:System.UIntPtr> являются типами указателей, которые используются для доступа к неуправляемой памяти. Если указатель не является закрытым, внутренним или доступным только для чтения, вредоносный код может изменить значение указателя, потенциально разрешение доступа к произвольным областям памяти или вызывая сбои приложения или системы.

 Если для защиты доступа к тип, содержащий поле указателя, см. в разделе [CA2112: Защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Обеспечьте безопасность указателя, сделав его только для чтения, внутренний или закрытый.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, если не следует полагаться на значение указателя.

## <a name="example"></a>Пример
 В следующем коде показано указатели, которые нарушают и удовлетворяют правилу. Обратите внимание на то, что не частных указателей также нарушают правило [CA1051: Не объявляйте видимые поля экземпляров](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2112: Защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: Не объявляйте видимые поля экземпляров](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>См. также
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>
