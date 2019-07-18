---
title: CA2147. Прозрачные методы могут не использовать утверждения безопасности
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36ae392173a18796c53100599fbf5f5fb5997beb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796862"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147. Прозрачные методы могут не использовать утверждения безопасности

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Код, помеченный как <xref:System.Security.SecurityTransparentAttribute> не предоставляется разрешение на утверждение.

## <a name="rule-description"></a>Описание правила
 Это правило анализирует все методы и типы в сборке, которая является либо 100% прозрачной, либо смешанной прозрачной и критической и пометить декларативное и императивное использование <xref:System.Security.CodeAccessPermission.Assert%2A>.

 Во время выполнения, все вызовы <xref:System.Security.CodeAccessPermission.Assert%2A> из прозрачного кода приведет к <xref:System.InvalidOperationException> исключение. Это может произойти в обе сборки, прозрачные на 100%, а также в смешанных прозрачной и критической сборок, где метод или тип объявляется прозрачным, но включает декларативное и императивное Assert.

 В .NET Framework 2.0 появилась функция с именем *прозрачности*. Отдельные методы, поля, интерфейсы, классы и типы могут быть либо прозрачный или.

 Прозрачный код не разрешено повышать уровень привилегий безопасности. Таким образом все разрешения, предоставленные или запрашиваемые автоматически передаются через код вызывающего объекта или узла домена приложения. Повышение примеры операторы Assert, требования LinkDemand, SuppressUnmanagedCode, и `unsafe` кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить эту проблему, либо пометить код, который вызывает Assert с <xref:System.Security.SecurityCriticalAttribute>, или удалить Assert.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте сообщение из этого правила.

## <a name="example"></a>Пример
 Этот код завершится ошибкой, если `SecurityTestClass` прозрачен, когда `Assert` вызывает метод <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>Пример
 Один из вариантов — Просмотр кода SecurityTransparentMethod в следующем примере и, если метод считается безопасным для повышения прав, пометьте SecurityTransparentMethod с secure критически важным. Для этого требуется, что подробные, исчерпывающие и без ошибок безопасности должна быть выполнена на метод вместе с вызовами, возникающих в рамках, чтобы метод Assert:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

 Другой вариант — удалить Assert из кода и разрешить все последующие файлы потока требования разрешение ввода-вывода за пределы метода SecurityTransparentMethod вызывающему. В результате проверок безопасности. В этом случае аудит безопасности необходим, так как запросы разрешений будут переданы вызывающему объекту или домена приложения. Запросы разрешений осуществляется посредством политики безопасности, среды размещения и код разрешений.

## <a name="see-also"></a>См. также
 [Предупреждения безопасности](../code-quality/security-warnings.md)