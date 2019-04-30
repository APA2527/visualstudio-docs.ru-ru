---
title: CA1812. Избегайте неиспользуемых внутренних классов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08d8b907e4a211b0735f07377c21dec1c0a982c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796908"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812. Избегайте неиспользуемых внутренних классов

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Экземпляр типа уровня сборки не создается кодом в сборке.

## <a name="rule-description"></a>Описание правила

Это правило пытается найти вызова одного из конструкторов типа и приводит к нарушению, если запрос не найден.

Это правило не проверяет следующие типы:

- Типы значений

- Абстрактные типы

- Перечисления

- Делегаты

- Типы массивов, определяемые компилятором

- Типы, не может быть создан и определяют `static` (`Shared` в Visual Basic) только для методов.

Если применить <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> к сборке, который анализируется, это правило не будет выполняться на каких-либо конструкторов, которые помечены как `internal` , так как невозможно определить, используется ли поле в другом `friend` сборки.

Несмотря на то, что не может обойти это ограничение в анализе кода Visual Studio, внешний инструмент FxCop автономного возникнет во внутренних конструкторах, если каждый `friend` сборка имеется в анализе.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, удалите тип или добавьте код, который его использует. Если тип содержит только статические методы, добавьте один из следующих к типу, чтобы запретить компилятору выполнять выпуска конструктор открытого экземпляра по умолчанию:

- Закрытый конструктор для типов, предназначенных для .NET Framework версий 1.0 и 1.1.

- `static` (`Shared` В Visual Basic) модификатор для типов, предназначенных [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила. Мы рекомендуем отключить предупреждение в следующих ситуациях:

- Класс создается через методы отражения с поздним связыванием, такие как <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- Класс создается автоматически средой выполнения или [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Например, классы, реализующие <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> или <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- Класс передается в качестве параметра универсального типа, имеющего нового ограничения. Например следующий пример вызывает это правило.

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }
    // [...]
    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

  В таких случаях мы рекомендуем отключить это предупреждение.

## <a name="related-rules"></a>Связанные правила

[CA1811: Не используйте Невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1801: Проверьте неиспользуемые параметры](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)