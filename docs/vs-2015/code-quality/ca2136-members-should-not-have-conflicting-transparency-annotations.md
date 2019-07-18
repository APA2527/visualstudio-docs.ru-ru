---
title: CA2136. Элементы не должны иметь конфликтующие пометки прозрачности | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b18ee5c048b0214779cdbe2635f5b7a14db8c28e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154308"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136. Члены не должны иметь противоречащие заметки прозрачности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Это правило срабатывает, когда член типа помечается <xref:System.Security> атрибут безопасности, чем атрибут безопасности контейнера элемента прозрачности.

## <a name="rule-description"></a>Описание правила
 Атрибуты прозрачности применяются из элементов кода большей области к элементам меньшей области. Атрибуты прозрачности элементов кода с большей областью имеют приоритет по сравнению с атрибутами прозрачности элементов кода, которые содержатся в первом элементе. Например, класс, помеченный с <xref:System.Security.SecurityCriticalAttribute> атрибута не может содержать метод, отмеченный атрибутом <xref:System.Security.SecuritySafeCriticalAttribute> атрибута.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить это нарушение, удалите атрибут безопасности из элемента кода, с меньшей областью или измените его атрибут должен совпадать с элемент кода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не следует отключать предупреждения из этого правила.

## <a name="example"></a>Пример
 В следующем примере метод, помеченный атрибутом <xref:System.Security.SecuritySafeCriticalAttribute> атрибут и он является членом класса, который помечен атрибутом <xref:System.Security.SecurityCriticalAttribute> атрибута. Безопасный атрибут должны быть удалены.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]
