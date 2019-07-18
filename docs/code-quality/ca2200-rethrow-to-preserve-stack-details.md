---
title: CA2200. Повторно порождайте исключения для сохранения сведений стека
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 55c58f098616a5c3c2d6ad72f56e8eda51f689be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796849"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200. Повторно порождайте исключения для сохранения сведений стека

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Исключение создается снова, и явным образом задается исключение в `throw` инструкции.

## <a name="rule-description"></a>Описание правила

Когда создается исключение, часть сведений, содержащихся в нем показана трассировка стека. Трассировка стека приведен список иерархии вызовов метода, который начинается с методом, который создает исключение и заканчивается на метод, который перехватывает исключение. Если создано исключение повторно, указав исключение в `throw` инструкции, трассировка стека перезапускается в текущего метода и список вызовов метода между исходным методом, создавшим исключение и текущим методом будет утерян. Чтобы сохранить исходные сведения о трассировке стека с исключением, используйте `throw` инструкции без указания исключения.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, заново создать исключение без явного указания исключения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример

В следующем примере показан метод `CatchAndRethrowExplicitly`, который нарушает правило и метод, `CatchAndRethrowImplicitly`, которой соблюдается правило.

[!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
[!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]