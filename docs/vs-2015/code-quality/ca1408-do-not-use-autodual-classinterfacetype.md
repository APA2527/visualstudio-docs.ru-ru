---
title: 'CA1408: не использовать двойное ClassInterfaceType | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3ccd8f9fa201e2cdfabfb7f6354d6df4718c572e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652752"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: не используйте AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Видимый тип модели COM помечен атрибутом <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>, для которого задано `AutoDual` значение <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Описание правила
 Типы, использующие сдвоенный интерфейс, позволяют клиентам выполнять привязку к определенному макету интерфейса. Все изменения в будущей версии макета типа и в базовых типах приведут к нарушению работы COM-клиентов, связанных с интерфейсом. По умолчанию, если атрибут <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> не указан, используется интерфейс диспетчеризации.

 Если не указано иное, все открытые неуниверсальные типы видимы для COM. все неоткрытые и универсальные типы являются невидимыми для COM.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените значение атрибута <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> на `None` значение <xref:System.Runtime.InteropServices.ClassInterfaceType> и явно определите интерфейс.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если только не уверены в том, что макет типа и его базовые типы не изменятся в следующей версии.

## <a name="example"></a>Пример
 В следующем примере показан класс, нарушающий правило, и повторное объявление класса для использования явного интерфейса.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/cs/FxCop.Interoperability.AutoDual.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/vb/FxCop.Interoperability.AutoDual.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1403: типы с автомакетом не должны быть видимыми для COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: помечайте интерфейсы ComSource как IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>См. также раздел
 [Введение в интерфейс класса,](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [соответствующий типам .NET для](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) взаимодействия [с неуправляемым кодом](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
