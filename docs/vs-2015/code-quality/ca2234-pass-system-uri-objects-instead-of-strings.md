---
title: CA2234. Передавайте объекты System.Uri вместо строк | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ce0ed8a2600d52d3a8f6649a528b6c809895f3fe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142404"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234. Передавайте объекты System.Uri вместо строк
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Выполняется вызов метода, содержит строковый параметр, имя которого содержит «uri», «Uri», «urn», «Urn», «url» или «Url»; и объявляющий тип метода содержит соответствующую перегрузку метода, имеющий <xref:System.Uri?displayProperty=fullName> параметра.

## <a name="rule-description"></a>Описание правила
 Имя параметра разделяется на лексемы, основывается на соглашении смешанный регистр знаков, а затем каждый маркер проверяется на соответствие «uri», «Uri», «urn», «Urn», «url» или «Url». Если есть совпадение имени, предполагается, что параметр представляет универсальный код ресурса (URI). В строковых представлениях кода URI часто встречаются ошибки синтаксического анализа и кодирования, которые могут привести к уязвимостям системы безопасности. <xref:System.Uri> Класс предоставляет аналогичные услуги надежным и безопасным способом. При наличии выбора между двумя перегрузками, которые отличаются лишь о представлениях кода URI, пользователь должен выбрать перегрузку, принимающую <xref:System.Uri> аргумент.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите перегрузку, принимающую <xref:System.Uri> аргумент.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если параметр строки не представляет URI.

## <a name="example"></a>Пример
 В следующем примере показан метод `ErrorProne`, который нарушает правило и метод, `SaferWay`, правильно вызывает <xref:System.Uri> перегрузки.

 [!code-cpp[FxCop.Usage.PassUri#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cpp/FxCop.Usage.PassUri.cpp#1)]
 [!code-csharp[FxCop.Usage.PassUri#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cs/FxCop.Usage.PassUri.cs#1)]
 [!code-vb[FxCop.Usage.PassUri#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/vb/FxCop.Usage.PassUri.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1057: Строка URI вызывают перегрузки System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: Свойства URI не должны быть строками](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: Параметры URI не должны быть строками](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI возвращать значения не должны быть строками](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
