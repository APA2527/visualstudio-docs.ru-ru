---
title: CA2104. Не объявляйте чтения только изменяемые ссылочные типы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a4c6619bc5803c1b44e1c6b0516987c3110bbd30
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687419"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104. Не объявляйте изменяющиеся ссылочные типы только для чтения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Видимый извне тип содержит видимое извне и доступное только для чтение поле, являющееся изменяемым ссылочным типом.

## <a name="rule-description"></a>Описание правила
 Изменяемый тип — это тип, экземпляр которого может быть изменен. <xref:System.Text.StringBuilder?displayProperty=fullName> Класс является примером изменяемый ссылочный тип. Он содержит члены, которые можно изменить значение экземпляра класса. Примером неизменяемого ссылочного типа является <xref:System.String?displayProperty=fullName> класса. После его создания экземпляра, его значение изменить нельзя.

 Модификатор доступа только для чтения ([readonly](https://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) в C# [ReadOnly](https://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], и [const](https://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) в C++) на ссылочный тип поля (указатель в C++) позволяет предотвратить поле заменены другой экземпляр ссылочного типа. Однако модификатор не препятствует данных экземпляра поля изменению посредством ссылочного типа.

 Поля только для чтения массивов будут исключены из этого правила, но вместо этого приведет к нарушению [CA2105: Поля массивов не должны считываться только](../code-quality/ca2105-array-fields-should-not-be-read-only.md) правило.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите модификатор только для чтения, или, если допустима критическое изменение, замените поле неизменяемый тип.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если тип поля является неизменяемым.

## <a name="example"></a>Пример
 В следующем примере объявление поля, которое вызывает нарушение этого правила.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]
