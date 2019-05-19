---
title: CA2231. Перегрузите оператор равенства на переопределяющем типе ValueType.Equals
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ec5f3bd1dfe66451ceff0b3af334a75aafb2e0b1
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841625"
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231. Перегрузите оператор равенства на переопределяющем типе ValueType.Equals

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|
|CheckId|CA2231|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип значения переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName> , но не реализует оператор равенства.

По умолчанию это правило считывает только типы, видимые извне, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

В большинстве языков программирования отсутствует реализация по умолчанию от оператора равенства (==) для типов значений. Если язык программирования поддерживает перегрузки операторов, следует реализовать оператор равенства. Его поведение должно быть идентично <xref:System.Object.Equals%2A>.

Оператор проверки на равенство по умолчанию нельзя использовать в перегруженной реализации оператора равенства. Это приведет к переполнению стека. Чтобы реализовать оператор равенства, используйте метод Object.Equals в реализации. Пример:

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, реализуйте оператор равенства.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила; Тем не менее мы рекомендуем по возможности укажите оператор равенства.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```ini
dotnet_code_quality.ca2231.api_surface = private, internal
```

В этой категории (использование), можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере определяется тип, который нарушает это правило:

[!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../code-quality/codesnippet/CSharp/ca2231-overload-operator-equals-on-overriding-valuetype-equals_1.cs)]

## <a name="related-rules"></a>Связанные правила

- [CA1046: Не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2225: Оператор дополнения с именами](../code-quality/ca2225-operator-overloads-have-named-alternates.md)
- [CA2226: Операторы должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224: Переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

## <a name="see-also"></a>См. также

- <xref:System.Object.Equals%2A?displayProperty=fullName>