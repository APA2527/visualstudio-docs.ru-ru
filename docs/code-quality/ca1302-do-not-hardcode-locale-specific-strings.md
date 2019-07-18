---
title: CA1302. Не указывайте прямо в коде строки, зависящие от языковых стандартов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a52add4453276ebf415b47f7f50e74b51a573306
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546535"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302. Не указывайте прямо в коде строки, зависящие от языковых стандартов

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод использует строковый литерал, представляющий часть путь к некоторым системным папкам.

## <a name="rule-description"></a>Описание правила
 <xref:System.Environment.SpecialFolder?displayProperty=fullName> Перечисление содержит члены, ссылающиеся на специальные системные папки. Расположение этих папок может иметь разные значения в различных операционных системах, пользователь может изменить некоторые из расположений и локализованы. Примером особая папка, которая является системной папке, который является «C:\WINDOWS\system32» на [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] , но «C:\WINNT\system32» на [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]. <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> Метод возвращает расположения, которые связаны с <xref:System.Environment.SpecialFolder> перечисления. Расположения, которые возвращаются <xref:System.Environment.GetFolderPath%2A> локализуются и подходит для текущего компьютера.

 Это правило размечает пути к папкам, которые извлекаются с помощью <xref:System.Environment.GetFolderPath%2A> метод в отдельном каталоге уровни. Каждый строковый литерал сравнивается с токенами. Если соответствие найдено, предполагается, что метод создает строку, ссылающуюся на расположение в системе, связанный с маркером. Для обеспечения переносимости и возможности локализации, используйте <xref:System.Environment.GetFolderPath%2A> метод для извлечения расположения специальные системные папки вместо строковых литералов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, получения расположения указывается с помощью <xref:System.Environment.GetFolderPath%2A> метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить предупреждение из этого правила, если строковый литерал не используется для ссылки на одну из системных папок, связанных с <xref:System.Environment.SpecialFolder> перечисления.

## <a name="example"></a>Пример
 Следующий пример создает путь к общей папке приложений, выдает три предупреждения из этого правила. Затем в примере извлекается путь с помощью <xref:System.Environment.GetFolderPath%2A> метод.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA1303: Не следует передавать литералы в виде локализованных параметров](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)