---
title: CA1006. Не создавайте вложенные универсальные типы в сигнатурах членов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 20bee606fd8cd98482a7304e068aaa7cbd5773a7
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923228"
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006. Не создавайте вложенные универсальные типы в сигнатурах членов

|||
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
Внешний видимый элемент имеет сигнатуру, содержащую аргумент вложенного типа.

## <a name="rule-description"></a>Описание правила
Аргумент вложенного типа также является аргументом универсального типа. Чтобы вызвать член, сигнатура которого содержит аргумент вложенного типа, пользователь должен создать экземпляр одного универсального типа и передать этот тип конструктору второго универсального типа. Это приводит к усложнению процедуры и синтаксиса, чего следует избегать.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, измените структуру, удалив аргумент вложенного типа.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует. Предоставление универсальных шаблонов в синтаксисе, который легко понять и использовать, сокращает время, необходимое для изучения и увеличения скорости внедрения новых библиотек.

## <a name="example"></a>Пример
В следующем примере показан метод, нарушающий правило, и синтаксис, который требуется для вызова нарушающего метода.

[!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
[!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]

## <a name="related-rules"></a>Связанные правила
[CA1005: Избегайте чрезмерных параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010 Коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Не объявляйте статические члены в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002 Не предоставляйте универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1004 Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Использование экземпляров универсальных обработчиков событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Используйте универсальные шаблоны там, где это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также
[Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)