---
title: CA2151. Поля с критическими типами должны быть критически важным для безопасности | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6c707efcc4c945e80ea0206cc5f30a647e83d231
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142590"
---
# <a name="ca2151-fields-with-critical-types-should-be-security-critical"></a>CA2151. Поля с критическими типами должны быть критическими с точки зрения безопасности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName||
|CheckId|CA2151|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Объявлено прозрачное для безопасности поле или поле, надежное с точки зрения безопасности. Его тип определяется как критический с точки зрения безопасности. Например:

```csharp
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      Type1 m_field; // CA2151, transparent field of critical type
   }
```

 В этом примере `m_field` — это прозрачное для безопасности поле критического с точки зрения безопасности типа.

## <a name="rule-description"></a>Описание правила
 Для использования критических с точки зрения безопасности типов код, который ссылается на тип, должен быть либо критическим с точки зрения безопасности, либо надежным с точки зрения безопасности. Это верно даже в случае косвенной ссылки. Например, при ссылке на прозрачное поле критического для безопасности типа код должен быть либо критическим с точки зрения безопасности, либо надежным с точки зрения безопасности. Поэтому применять прозрачное для безопасности поле или поле, надежное с точки зрения безопасности, не рекомендуется, поскольку прозрачный код по-прежнему не сможет получить доступ к полю.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, отметьте поле атрибутом <xref:System.Security.SecurityCriticalAttribute> или сделайте тип, на который ссылается поле, прозрачным с точки зрения безопасности либо надежным с точки зрения безопасности.

```csharp
// Fix 1: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }

// Fix 2: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   class Type1 { } // Type1 is now transparent

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }
```

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Комментарии
