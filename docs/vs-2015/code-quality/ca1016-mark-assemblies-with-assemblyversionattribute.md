---
title: CA1016. Помечать сборки атрибутом AssemblyVersionAttribute | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4fbe2ef81dbb1dd5be15b6a0ac4b8cc1df96206a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62424015"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016. Пометьте сборки с помощью AssemblyVersionAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Сборка имеет номер версии.

## <a name="rule-description"></a>Описание правила
 Удостоверение сборки представляет собой следующую информацию:

- Имя сборки

- Номер версии

- culture

- Открытый ключ (для сборок со строгими именами).

  [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] использует номер версии для уникального обозначения сборки и для привязки к типам в сборках со строгими именами. Номер версии используется наряду с политикой версий и издателя. По умолчанию приложения выполняются только с версией сборки, которая использовалась для их построения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте номер версии сборки с помощью <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> атрибута. См. следующий пример.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила для сборок, используемых сторонними производителями или в рабочей среде.

## <a name="example"></a>Пример
 В следующем примере показано сборку, которая имеет <xref:System.Reflection.AssemblyVersionAttribute> применен атрибут.

 [!code-cpp[FxCop.Design.AssembliesVersion#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cpp/FxCop.Design.AssembliesVersion.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cs/FxCop.Design.AssembliesVersion.cs#1)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/vb/FxCop.Design.AssembliesVersion.vb#1)]

## <a name="see-also"></a>См. также
 [Управление версиями сборок](http://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [как: Создание политики издателя](http://msdn.microsoft.com/library/8046bc5d-2fa9-4277-8a5e-6dcc96c281d9)
