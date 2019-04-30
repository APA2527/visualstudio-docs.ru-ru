---
title: CA1819. Свойства не должны возвращать массивы
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 11209ec181e2c2b61c7767787ee99c2d69eabe8b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545567"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819. Свойства не должны возвращать массивы

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Категория|Microsoft.Performance|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Свойство возвращает массив.

По умолчанию это правило считывает только видимое извне свойств и типов, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Массивы, возвращаемые свойства не защищен от записи, даже если свойство доступно только для чтения. Чтобы защитить массив от изменений, свойство должно возвращать копию массива. Как правило пользователи не понимают требований к производительности вызова такого свойства. В частности они могут использовать свойство как индексированное свойство.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, сделайте свойство метод или измените свойства для возврата коллекции.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Можно подавить предупреждение, которое возникает для свойства атрибута, который является производным от <xref:System.Attribute> класса. Атрибуты могут содержать свойства, которые возвращают массивы, но не могут содержать свойства, которые возвращают коллекции.

Можно отключить предупреждение, если свойство является частью [объект передачи данных (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) класса.

В противном случае не отключайте предупреждение из этого правила.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```
dotnet_code_quality.ca1819.api_surface = private, internal
```

В этой категории (производительность), можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Пример нарушения

В следующем примере показано свойство, которое нарушает это правило:

[!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
[!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

Чтобы устранить нарушение этого правила, сделайте свойство метод или измените свойства для возврата коллекции вместо массива.

### <a name="change-the-property-to-a-method"></a>Измените свойство на метод

В следующем примере устраняется нарушение, изменив свойство в метод:

[!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
[!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

### <a name="change-the-property-to-return-a-collection"></a>Измените значение свойства для возврата коллекции

В следующем примере нарушение устраняется путем изменения свойства для возврата <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>:

[!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
[!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allow-users-to-modify-a-property"></a>Разрешить пользователям изменять свойство

Может потребоваться предоставить пользователю класса, для изменения свойства. В следующем примере показано свойство чтения/записи, которое нарушает это правило:

[!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
[!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

В следующем примере нарушение устраняется путем изменения свойства для возврата <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>:

[!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
[!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>Связанные правила

- [CA1024: Используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)