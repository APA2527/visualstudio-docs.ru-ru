---
title: CA1014. Пометьте сборки с помощью CLSCompliantAttribute
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0ea7c0d4b9c1d8edea3c2d96f04114db47f3b0d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779512"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014. Пометьте сборки с помощью CLSCompliantAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Сборка не имеет <xref:System.CLSCompliantAttribute?displayProperty=fullName> атрибут, примененный к нему.

## <a name="rule-description"></a>Описание правила
 Спецификация среды CLS определяет ограничения по именованию, типам данных и правилам, которым должны соответствовать сборки, предназначенные для использования в нескольких языках программирования. Хороший проект определяет, что все сборки явным образом указывать совместимость с CLS с <xref:System.CLSCompliantAttribute>. Если атрибут отсутствует в сборке, сборка не является совместимым.

 Это возможность CLS-совместимые сборки содержат типы или члены, которые не соответствуют типов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте атрибут к сборке. Вместо пометки всей сборки считается несоответствующим, следует определить, какие типы или члены типов не являются совместимыми и пометить их таким образом. Если это возможно необходимо предоставить CLS-совместимая альтернатива для несовместимых элементов таким образом, чтобы максимально широкой аудиторией доступны все функции сборки.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Если не хотите, чтобы сборка должна быть совместимым, примените атрибут и присвойте ему значение `false`.

## <a name="example"></a>Пример
 В следующем примере показано сборку, которая имеет <xref:System.CLSCompliantAttribute?displayProperty=fullName> применен атрибут, который они объявлены CLS-совместимыми.

 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>См. также

- <xref:System.CLSCompliantAttribute?displayProperty=fullName>
- [Независимость от языка и независимые от языка компоненты](/dotnet/standard/language-independence-and-language-independent-components)