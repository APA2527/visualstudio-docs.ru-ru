---
title: Набор правил "Базовые нормы и правила разработки" для управляемого кода
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7c2a9570eeae6d9545bb91f7f1ed0c57df3a9c92
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62571372"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Набор правил "Базовые нормы и правила разработки" для управляемого кода
Можно использовать базовые правила и рекомендации по разработке Microsoft набора правил в сосредоточиться на создании кода проще для понимания и использования. Следует включить это правило, если проект содержит библиотечный код или если вы хотите принудительное применение рекомендаций для кода, который легко поддерживать.

 Базовые нормы и правила разработки включают все правила в наборе правил минимальные правила Майкрософт. Список правил в минимальном, см. в разделе [набора правил управляемых рекомендуемые правила для управляемого кода](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md).

 В следующей таблице описаны все правила в наборе правил Microsoft базовые нормы и правила разработки.

|Правило|Описание|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Правильно объявляйте обработчики событий|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Пометьте сборки с помощью AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Методы интерфейса должны быть доступны для вызова дочерними типами|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Переместите методы P/Invoke в класс NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Не скрывайте методы базовых классов|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Правильно реализуйте IDisposable|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Не вызывайте исключения в непредвиденных местах|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Избегайте повторяющихся акселераторов|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Для методов P/Invoke должны существовать точки входа|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Методы P/Invoke не должны быть видимыми|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Типы с автомакетом не должны быть видимыми для COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Вызывайте GetLastError сразу после P/Invoke|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Базовые типы, относящиеся к типу, видимому для COM, должны быть видимыми для COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Методы регистрации COM должны быть согласованными|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Правильно объявляйте методы P/Invoke|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Удалите пустые методы завершения|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Поля типов значений должны быть переносимыми|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Объявления P/Invoke должны быть переносимыми|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Не блокируйте объекты с ненадежными удостоверениями|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Проверьте запросы SQL на наличие уязвимостей системы безопасности|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Укажите тип маршалинга для строковых аргументов P/Invoke|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Проверьте объявляемые параметры безопасности типов значений|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Указатели не должны быть видимыми|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Защищенные типы не должны предоставлять поля|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Безопасность метода должна быть надмножеством типа|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA-методы должны вызывать только APTCA-методы|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA-типы должны расширять только базовые APTCA-типы|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Не используйте косвенное представление методов с требованиями ссылки|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Переопределяющие требования ссылки должны быть идентичны базовым|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Ограничьте уязвимые предложения finally во внешних блоках try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Для требований ссылок на тип необходимы требования наследования|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Критические для безопасности типы не могут участвовать в эквивалентности типов|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Конструкторы по умолчанию должны быть по меньшей мере такими же критическими, как конструкторы по умолчанию базового типа|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Делегаты должны быть привязаны к методам с соответствующей прозрачностью|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Методы должны сохранять одинаковую прозрачность при переопределении базовых методов|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Прозрачные методы должны содержать только поддающийся проверке промежуточный язык|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Прозрачный код не должен ссылаться на критические для безопасности элементы|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Прозрачные методы не должны удовлетворять требования LinkDemand|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Типы должны быть по крайней мере настолько же критическими, как их базовые типы и интерфейсы|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Прозрачные методы могут не использовать утверждения безопасности|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Прозрачные методы не должны вызывать машинный код|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Повторно порождайте исключения для сохранения сведений стека|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Не ликвидируйте объекты несколько раз|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Используйте встроенную инициализацию статических полей типов значений|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Не помечайте обслуживаемые компоненты с помощью WebMethod|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Следует высвобождать высвобождаемые поля|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Не вызывайте переопределяемые методы в конструкторах|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Высвобождаемые типы должны объявлять методы завершения|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Методы завершения должны вызывать метод завершения базового класса|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Реализуйте конструкторы сериализации|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Перегрузите оператор равенства на переопределяющем типе ValueType.Equals|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Отметьте точки входа Windows Forms меткой STAThread|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Пометьте все несериализуемые поля|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Вызывайте методы базового класса для типов ISerializable|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Пометьте типы ISerializable атрибутом SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Правильно реализуйте методы сериализации|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Правильно реализуйте ISerializable|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Задайте правильные аргументы для методов форматирования|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Правильно выполняйте проверку NaN|
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Не объявляйте статические члены в универсальных типах|
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|Не предоставляйте универсальные списки|
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|Используйте экземпляры обработчика универсальных событий|
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Универсальные методы должны предоставлять параметр типа|
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Не используйте слишком много параметров в универсальных типах|
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Не создавайте вложенные универсальные типы в сигнатурах членов|
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|По возможности используйте универсальные объекты|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Перечисляемые типы должны иметь нулевое значение|
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Коллекции должны реализовать универсальный интерфейс|
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Попробуйте передать базовые типы в качестве параметров|
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Абстрактные типы не должны иметь конструкторы|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Перегружайте оператор равенства при перегрузке операторов сложения и вычитания|
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Пометьте сборки с помощью CLSCompliantAttribute|
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Пометьте сборки с помощью ComVisibleAttribute|
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Пометьте атрибуты с помощью AttributeUsageAttribute|
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Определите методы доступа для аргументов атрибута|
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Индексы не должны быть многомерными|
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|По возможности используйте свойства|
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Замените повторяющиеся аргументы массивом параметров|
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|Не следует использовать параметры по умолчанию|
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Пометьте перечисляемые типы с помощью FlagsAttribute|
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|Хранилище перечисляемых типов должно относиться к типу Int32|
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|По возможности используйте события|
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Не перехватывайте типы общих исключений|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Реализуйте стандартные конструкторы исключений|
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Вложенные типы не должны быть видимыми|
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|В составе реализаций ICollection есть члены со строгим типом|
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Переопределите методы в сопоставимых типах|
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Перечислители должны иметь строгие типы|
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Списки имеют строгие типы|
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|Укажите сообщение ObsoleteAttribute|
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Используйте целый или строковый аргумент для индексаторов|
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Свойства не должны быть доступными только для записи|
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Не перегружайте оператор равенства для ссылочных типов|
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Не объявляйте защищенные члены в запечатанных типах|
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Не объявляйте виртуальные члены в запечатанных типах|
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Объявите типы в пространствах имен|
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Не объявляйте видимые поля экземпляров|
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Типы со статическими заполнителями должны быть запечатаны|
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Типы со статическими заполнителями не должны иметь конструкторы|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Параметры URI не должны быть строками|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Возвращаемые значения URI не должны быть строками|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Свойства URI не должны быть строками|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Перегрузки строковых параметров URI вызывают перегрузки System.Uri|
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Типы не должны расширять определенные базовые типы|
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Члены не должны предоставлять определенные конкретные типы|
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|Исключения должны быть общими|
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Имена переменных не должны совпадать с именами полей|
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Избегайте чрезмерной сложности|
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Идентификаторы должны отличаться не только прописными и строчными буквами|
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Идентификаторы не должны совпадать с ключевыми словами|
|[CA1801](../code-quality/ca1801-review-unused-parameters.md)|Проверьте неиспользуемые параметры|
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Удалите неиспользуемые локальные переменные|
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Избегайте лишних локальных переменных|
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Инициализируйте статические поля ссылочных типов при объявлении|
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Избегайте невызываемого частного кода|
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Избегайте неиспользуемых внутренних классов|
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Избегайте незапечатанных атрибутов|
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Используйте массивы массивов вместо многомерных массивов|
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Переопределяйте операторы Equals и равенства для типов значений|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Свойства не должны возвращать массивы|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Проверяйте наличие пустых строк, используя длину строки|
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|Пометьте члены как статические|
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Избегайте неиспользуемых частных полей|
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Не порождайте исключения зарезервированных типов|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Используйте управляемые эквиваленты Win32 API|
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Правильно создавайте экземпляры исключений аргументов|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Поля, не являющиеся константами, не должны быть видимыми|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Не помечайте перечисляемые типы с помощью FlagsAttribute|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|В предложениях с исключениями не должны порождаться исключения|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Методы завершения должны быть защищенными|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Не уменьшайте видимость наследуемого члена|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Члены должны различаться не только возвращаемым типом|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Переопределяйте Equals при перегрузке оператора равенства|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Для перегрузок операторов существуют варианты с именами|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Перегрузки операторов должны быть симметричными|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Свойства, возвращающие коллекции, должны быть доступными только для чтения|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Используйте параметры для аргументов переменной|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Передавайте объекты System.Uri вместо строк|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Обеспечьте наличие методов десериализации в необязательных полях|