---
title: CA1721. Методы get не должны совпадать с именами свойств | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 94d120a7656fc9270543ceeb57063124764c4bca
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431188"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721. Имена свойств не должны совпадать с именами методов get
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя открытого или защищенного элемента начинается с «Get» и в противном случае соответствует имени открытого или защищенного свойства. Например типом, который содержит метод с именем «GetColor» и свойство с именем «Цвет» нарушает это правило.

## <a name="rule-description"></a>Описание правила
 Методы get и свойства должны иметь имена, четко различать их функции.

 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает время, которое требуется изучать новую библиотеку программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Измените имя, чтобы он не соответствует имени метода, который добавляется префикс «Get».

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

> [!NOTE]
> Это предупреждение можно не указывать, если вызвана реализация интерфейса IExtenderProvider метод Get.

## <a name="example"></a>Пример
 В следующем примере содержится метод и свойство, которое нарушает это правило.

 [!code-csharp[FxCop.Naming.GetMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/cs/FxCop.Naming.GetMethod.cs#1)]
 [!code-vb[FxCop.Naming.GetMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/vb/FxCop.Naming.GetMethod.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1024: Используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)
