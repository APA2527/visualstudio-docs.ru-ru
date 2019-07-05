---
title: CA1009. Правильно объявите обработчики событий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 51b04b4c081bd7961ef26657dd3cb526652df568
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704254"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009. Правильно объявляйте обработчики событий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Делегат, обрабатывающий событие открытый или защищенный не имеет правильной сигнатуры, возвращаемого типа или имена параметров.

## <a name="rule-description"></a>Описание правила
 Методы обработчиков событий принимают два параметра. Первый — типа <xref:System.Object?displayProperty=fullName> и называется «отправителя». Это объект, вызвавший событие. Второй параметр имеет тип <xref:System.EventArgs?displayProperty=fullName> и называется «e». Это данные, связанные с событием. Например если событие возникает каждый раз, когда файл открыт, данные события обычно содержит имя файла.

 Методы обработчика событий не должны возвращать значение. В языке C# оно обозначается типом возвращаемого `void`. Обработчик событий может вызывать несколько методов в нескольких объектах. Если методы было разрешено для возврата значения, будет возникать несколькими возвращаемыми значениями для каждого события и только значение последнего метода, вызванного бы быть доступны.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, исправьте подпись, тип возвращаемого значения или имена параметров делегата. Дополнительные сведения см. следующий пример.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано делегат, который подходит для обработки событий. Методы, которые могут быть вызваны этот обработчик событий соответствует подписи, который указан в руководствах по разработке. `AlarmEventHandler` — Имя типа делегата. `AlarmEventArgs` является производным от базового класса данных о событиях, <xref:System.EventArgs>, и содержит alarm данные события.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2109: Проверьте видимые обработчики событий](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>См. также
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [NIB: События и делегаты](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
