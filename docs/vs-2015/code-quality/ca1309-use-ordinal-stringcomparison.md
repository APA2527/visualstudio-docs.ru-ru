---
title: CA1309. Используйте порядковый параметр StringComparison | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7b491cf06528b67c96f90f314210e61800e0cab1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200342"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309. Используйте порядковый параметр StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Не задает операции сравнения строк, являющаяся лингвистической <xref:System.StringComparison> параметра к **порядковый номер** или **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Описание правила
 Многие строковые операции, наиболее важных <xref:System.String.Compare%2A?displayProperty=fullName> и <xref:System.String.Equals%2A?displayProperty=fullName> теперь предоставляют перегрузку, принимающую <xref:System.StringComparison?displayProperty=fullName> значение перечисления в качестве параметра.

 Необходимо указывать оба **StringComparison.Ordinal** или **StringComparison.OrdinalIgnoreCase**, то строковое сравнение будет лингвистической. То есть при сравнение решения принимаются функции, характерные для естественного языка игнорируются. Это означает, что решения основаны на основе простых байтовых сравнений и игнорировать таблиц регистров или эквивалентности, которые параметризуются языком и региональными параметрами. Таким образом, путем явного задания для параметра либо **StringComparison.Ordinal** или **StringComparison.OrdinalIgnoreCase**, кода часто скорость, повышает правильность и становится более надежным.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените метод сравнения строк на перегрузку, принимающую <xref:System.StringComparison?displayProperty=fullName> перечисления в качестве параметра и задавать либо **порядковый номер** или **OrdinalIgnoreCase**. Например, измените `String.Compare(str1, str2)` на `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если библиотека или приложение предназначено для ограниченной локальной аудитории или в случаях, когда следует использовать семантику текущего языка и региональных параметров.

## <a name="see-also"></a>См. также
 [Предупреждения глобализации](../code-quality/globalization-warnings.md) [CA1307: Укажите StringComparison](../code-quality/ca1307-specify-stringcomparison.md)
