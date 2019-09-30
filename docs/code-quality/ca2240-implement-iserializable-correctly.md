---
title: CA2240. Правильно реализуйте ISerializable
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2640fddcde0d8777363a3c56e398e7ff307a20c7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237881"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240. Правильно реализуйте ISerializable

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Тип, видимый извне, может быть назначен <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейсу, и одно из следующих условий имеет значение true:

- Тип наследует, но не переопределяет <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> метод, а тип объявляет поля экземпляра, не помеченные <xref:System.NonSerializedAttribute?displayProperty=fullName> атрибутом.

- Тип не запечатан, и тип реализует <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод, который не является видимым и переопределяемым извне.

## <a name="rule-description"></a>Описание правила
Поля экземпляров, объявленные в типе, который наследует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс, не включаются автоматически в процесс сериализации. Чтобы включить поля, тип должен реализовывать <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод и конструктор сериализации. Если поля не должны быть сериализованы, примените <xref:System.NonSerializedAttribute> атрибут к полям, чтобы явно указать решение.

В незапечатанных типах реализации <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метода должны быть видимыми извне. Таким образом, метод может вызываться производными типами и быть переопределяемым.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, сделайте <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод видимым и переопределяемым и убедитесь, что все поля экземпляра включены в процесс сериализации или явно помечены <xref:System.NonSerializedAttribute> атрибутом.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показаны два сериализуемых типа, которые нарушают правило.

[!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
[!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
[!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>Пример
Следующий пример устраняет два предыдущих нарушения, предоставляя переопределяемую реализацию <xref:System.Runtime.Serialization.ISerializable.GetObjectData> для класса Book и предоставляя `GetObjectData` реализацию для класса Library.

[!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
[!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>Связанные правила

- [CA2236: Вызов методов базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2238: Правильно реализуйте методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2235. Пометьте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)
- [CA2237. Пометьте типы ISerializable с SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2239: Предоставление методов десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2120: Безопасные конструкторы сериализации](../code-quality/ca2120-secure-serialization-constructors.md)