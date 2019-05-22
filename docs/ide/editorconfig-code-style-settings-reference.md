---
title: Параметры соглашений о написании кода .NET в EditorConfig
ms.date: 06/14/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: kuhlenh
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a5778764bb065ae6da53016c2c9bbb557db20c51
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65847379"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Параметры соглашений о написании кода .NET в EditorConfig

Вы можете описать и поддерживать согласованный стиль кода в своей базе кода с помощью файла [EditorConfig](../ide/create-portable-custom-editor-options.md). EditorConfig содержит несколько ключевых свойств форматирования, таких как `indent_style` и `indent_size`. В Visual Studio параметры соглашений о написании кода .NET можно настроить в файле EditorConfig. Вы можете включить или отключить отдельные соглашения о написании кода .NET и настроить строгость применения каждого правила с помощью уровней серьезности.

> [!TIP]
> - При определении соглашения о написании кода в файле .editorconfig вы можете настроить способ анализа вашего кода [анализаторами стиля кода](../code-quality/roslyn-analyzers-overview.md), которые встроены в Visual Studio. Файл .editorconfig — это файл конфигурации для таких анализаторов.
> - Предпочтения по стилю кода для Visual Studio также можно задать в диалоговом окне [Параметры текстового редактора](code-styles-and-code-cleanup.md). Но при этом параметры в файле .editorconfig имеют приоритет, и предпочтения, заданные вами в меню **Параметры** не связываются с определенным проектом.

В конце этой статьи приведен [пример файла .editorconfig](#example-editorconfig-file).

## <a name="convention-categories"></a>Категории соглашений

В .NET поддерживаются следующие три категории соглашений о написании кода.

- [Стили кода языка](#language-code-styles)

   Правила, распространяющиеся на язык C# или Visual Basic. Например, вы можете указать правила использования `var` или явных типов при определении переменных или назначении приоритета элементам, воплощающим выражение.

- [Соглашения по форматированию](#formatting-conventions)

   Правила, описывающие макет и структуру кода для повышения его читаемости. Например, вы можете указать правила для стиля скобок Олмана или назначения приоритета пробелам в блоках управления.

- [Соглашения об именовании](../ide/editorconfig-naming-conventions.md)

   Правила, описывающие именование элементов кода. Например, можно указать, что методы `async` должны оканчиваться на "Async".

## <a name="language-code-styles"></a>Стили кода языка

Правила для стилей кода языка имеют следующий формат:

`options_name = false|true : none|silent|suggestion|warning|error`

Для каждого правила стиля кода языка нужно указать **true** (предпочитать этот стиль) или **false** (не предпочитать этот стиль), а также уровень **серьезности**. Серьезность означает требуемый уровень применения для этого стиля.

Следующая таблица описывает возможные значения серьезности и их влияние:

Серьезность | Действие
:------- | ------
`none` | При нарушении этого правила пользователю не выводится никаких данных. Однако функции создания кода будут генерировать код в этом стиле. Правила с уровнем серьезности `none` никогда не появляются в меню **Быстрые действия и операции рефакторинга**. В большинстве случаев это воспринимается как "отключено" или "игнорируется".
`silent` (также `refactoring` в Visual Studio 2017 версии 15.8) | При нарушении этого правила пользователю не выводится никаких данных. Однако функции создания кода будут генерировать код в этом стиле. Правила с уровнем серьезности `silent` участвуют в очистке, а также появляются в меню **Быстрые действия и операции рефакторинга**.
`suggestion` | При несоблюдении этого правила стиля пользователю выводится предложение. Предложения отображаются в виде трех серых точек под первыми двумя символами.
`warning` | При несоблюдении этого правила стиля выводится предупреждение компилятора.
`error` | При несоблюдении этого правила стиля выводится ошибка компилятора.

В следующем списке приведены допустимые правила стилей кода языка:

- Параметры стиля кода .NET
    - [Квалификаторы "This." и "Me."](#this_and_me)
        - dotnet\_style\_qualification\_for_field
        - dotnet\_style\_qualification\_for_property
        - dotnet\_style\_qualification\_for_method
        - dotnet\_style\_qualification\_for_event
    - [Ключевые слова языка вместо имен типов .NET Framework для ссылок на типы](#language_keywords)
        - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
        - dotnet\_style\_predefined\_type\_for\_member_access
    - [Предпочтения для модификаторов](#normalize_modifiers)
        - dotnet\_style\_require\_accessibility_modifiers
        - csharp\_preferred\_modifier_order
        - visual\_basic\_preferred\_modifier_order
        - dotnet\_style\_readonly\_field
    - [Предпочтения относительно круглых скобок](#parentheses)
        - dotnet\_style\_parentheses\_in\_arithmetic\_binary\_operators
        - dotnet\_style\_parentheses\_in\_other\_binary\_operators
        - dotnet\_style\_parentheses\_in\_other\_operators
        - dotnet\_style\_parentheses\_in\_relational\_binary\_operators
    - [Настройки уровня выражений](#expression_level)
        - dotnet\_style\_object_initializer
        - dotnet\_style\_collection_initializer
        - dotnet\_style\_explicit\_tuple_names
        - dotnet\_style\_prefer\_inferred\_tuple_names
        - dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names
        - dotnet\_style\_prefer\_auto\_properties
        - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method
        - dotnet\_style\_prefer\_conditional\_expression\_over\_assignment
        - dotnet\_style\_prefer\_conditional\_expression\_over\_return
    - [Настройки проверки Null](#null_checking)
        - dotnet\_style\_coalesce_expression
        - dotnet\_style\_null_propagation
- Параметры стиля кода C#
    - [Неявные и явные типы](#implicit-and-explicit-types)
        - csharp\_style\_var\_for\_built\_in_types
        - csharp\_style\_var\_when\_type\_is_apparent
        - csharp\_style\_var_elsewhere
    - [Элементы, воплощающие выражение](#expression_bodied_members)
        - csharp\_style\_expression\_bodied_methods
        - csharp\_style\_expression\_bodied_constructors
        - csharp\_style\_expression\_bodied_operators
        - csharp\_style\_expression\_bodied_properties
        - csharp\_style\_expression\_bodied_indexers
        - csharp\_style\_expression\_bodied_accessors
    - [Сопоставление шаблонов](#pattern_matching)
        - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
        - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
    - [Встроенные объявления переменных](#inlined_variable_declarations)
        - csharp\_style\_inlined\_variable_declaration
    - [Настройки уровня выражений](#expression_level_csharp)
        - csharp\_prefer\_simple\_default_expression
        - csharp\_style\_deconstructed\_variable_declaration
        - csharp\_style\_pattern\_local\_over\_anonymous_function
    - [Настройки проверки Null](#null_checking_csharp)
        - csharp\_style\_throw_expression
        - csharp\_style\_conditional\_delegate_call
    - [Настройки блока кода](#code_block)
        - csharp\_prefer_braces

### <a name="net-code-style-settings"></a>Параметры стиля кода .NET

Правила стилей в этом разделе относятся как к C#, так и к Visual Basic. Чтобы просмотреть примеры кода на предпочитаемом языке программирования, выберите его в раскрывающемся меню **Язык** в правом верхнем углу окна браузера.

#### <a name="this_and_me"></a>Квалификаторы "This." и "Me."

Это правило стиля (идентификаторы правила IDE0003 и IDE0009) может применяться к полям, свойствам, методам или событиям. Значение **true** означает, что перед символом кода предпочтительно добавлять `this.` в C# или `Me.` в Visual Basic. Значение **false** означает, что перед символом кода предпочтительно _не_ добавлять `this.` или `Me.`.

В следующей таблице указаны имена правил, применяемые языки программирования и значения по умолчанию:

| Имя правила | Применимые языки | Значение по умолчанию в Visual Studio |
| ----------- | -------------------- | ----------------------|
| dotnet_style_qualification_for_field | C# и Visual Basic | false:silent |
| dotnet_style_qualification_for_property | C# и Visual Basic | false:silent |
| dotnet_style_qualification_for_method | C# и Visual Basic | false:silent |
| dotnet_style_qualification_for_event | C# и Visual Basic | false:silent |

**dotnet\_style\_qualification\_for_field**

- Когда для этого правила задано значение **true**, то перед полями предпочтительно добавлять `this.` в C# или `Me.` в Visual Basic.
- Когда для этого правила задано значение **false**, то перед полями предпочтительно _не_ добавлять `this.` или `Me.`.

Примеры кода:

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```

```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```

**dotnet\_style\_qualification\_for_property**

- Когда для этого правила задано значение **true**, то перед свойствами предпочтительно добавлять `this.` в C# или `Me.` в Visual Basic.
- Когда для этого правила задано значение **false**, то перед свойствами предпочтительно _не_ добавлять `this.` или `Me.`.

Примеры кода:

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```

```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```

**dotnet\_style\_qualification\_for_method**

- Когда для этого правила задано значение **true**, то перед методами предпочтительно добавлять `this.` в C# или `Me.` в Visual Basic.
- Когда для этого правила задано значение **false**, то перед методами предпочтительно _не_ добавлять `this.` или `Me.`.

Примеры кода:

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```

```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```

**dotnet\_style\_qualification\_for_event**

- Когда для этого правила задано значение **true**, то перед событиями предпочтительно добавлять `this.` в C# или `Me.` в Visual Basic.
- Когда для этого правила задано значение **false**, то перед событиями предпочтительно _не_ добавлять `this.` или `Me.`.

Примеры кода:

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```

```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```

В файле *EDITORCONFIG* эти правила могут иметь следующий вид:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="language_keywords"></a>Ключевые слова языка вместо имен типов .NET Framework для ссылок на типы

Это правило стиля можно применить к локальным переменным, параметрам методов и членам классов, а также в виде отдельного правила для ввода выражений доступа к члену. Значение **true** означает предпочтение ключевого слова языка (например, `int` или `Integer`) вместо имени типа (например, `Int32`) для типов, которые представляет ключевое слово. Значение **false** означает предпочтение имени типа вместо ключевого слова языка.

В следующей таблице указаны имена и идентификаторы правил, применяемые языки программирования и значения по умолчанию:

| Имя правила | Идентификатор правила | Применимые языки | Значение по умолчанию в Visual Studio |
| --------- | ------- | -------------------- | ----------------------|
| dotnet_style_predefined_type_for_locals_parameters_members | IDE0012 и IDE0014 | C# и Visual Basic | true:silent |
| dotnet_style_predefined_type_for_member_access | IDE0013 и IDE0015 | C# и Visual Basic | true:silent |

**dotnet\_style\_predefined\_type\_for\_locals\_parameters_members**

- Когда это правило имеет значение **true**, предпочтение отдается ключевому слову языка для локальных переменных, параметров методов и членов классов вместо имени типа для типов, имеющих представляющее их ключевое слово.
- Когда это правило имеет значение **false**, предпочтение отдается имени типа для локальных переменных, параметров методов и членов классов вместо ключевого слова языка.

Примеры кода:

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```

```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
```

**dotnet\_style\_predefined\_type\_for\_member_access**

- Когда это правило имеет значение **true**, предпочтение отдается ключевому слову языка для выражений доступа к члену вместо имени типа для типов, имеющих представляющее их ключевое слово.
- Когда это правило имеет значение **false**, предпочтение отдается имени типа для выражений доступа к члену вместо ключевого слова языка.

Примеры кода:

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```

```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```

В файле *EDITORCONFIG* эти правила могут иметь следующий вид:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="normalize_modifiers"></a>Предпочтения для модификаторов

Этот раздел приводит предпочтительные правила стиля для модификаторов, в том числе когда требуются модификаторы доступа, указывается предпочтительный порядок сортировки или требуется модификатор только для чтения.

В следующей таблице указаны имена и идентификаторы правил, применяемые языки программирования, значения по умолчанию и первая поддерживаемая версия Visual Studio:

| Имя правила | Идентификатор правила | Применимые языки | Значение по умолчанию в Visual Studio | Версия Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| dotnet_style_require_accessibility_modifiers | IDE0040 | C# и Visual Basic | for_non_interface_members:silent | 15.5 |
| csharp_preferred_modifier_order | IDE0036 | C# | public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent | 15.5 |
| visual_basic_preferred_modifier_order | IDE0036 | Visual Basic | Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent | 15.5 |
| dotnet_style_readonly_field | IDE0044 | C# и Visual Basic | true:suggestion | 15.7 |

**dotnet\_style\_require\_accessibility_modifiers**

Это правило принимает значение из следующей таблицы:

| Значение | Описание |
| ----- |:----------- |
| always | Сделать предпочтительным указание модификаторов доступа |
| for\_non\_interface_members | Предпочтительно объявление модификаторов доступа, за исключением членов открытого интерфейса. (Аналогично значению **always** и будет использоваться при наличии методов интерфейса C# по умолчанию.) |
| never | Предпочитать не указывать модификаторы доступа |
| omit_if_default | Сделать предпочтительным указание модификаторов доступа, если только они не являются модификаторами по умолчанию. |

Примеры кода:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst = "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst = "constant";
}
```

**csharp_preferred_modifier_order**

- Если это правило задано для списка модификаторов, предпочитать указанный порядок.
- Если это правило пропущено в файле, не предпочитать порядок модификаторов.

Примеры кода:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

**visual_basic_preferred_modifier_order**

- Если это правило задано для списка модификаторов, предпочитать указанный порядок.
- Если это правило пропущено в файле, не предпочитать порядок модификаторов.

Примеры кода:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

**dotnet_style_readonly_field**

- Если это правило имеет значение **true**, укажите, что поля должны иметь метку `readonly` (C#) или `ReadOnly` (Visual Basic), если они встроены или находятся внутри конструктора.
- Если это правило имеет значение **false**, укажите, что неважно, будут ли поля иметь метку `readonly` (C#) или `ReadOnly` (Visual Basic).

Примеры кода:

```csharp
// dotnet_style_readonly_field = true
class MyClass
{
    private readonly int _daysInYear = 365;
}
```

```vb
' dotnet_style_readonly_field = true
Public Class MyClass
    Private ReadOnly daysInYear As Int = 365
End Class
```

В файле *EDITORCONFIG* эти правила могут иметь следующий вид:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion
dotnet_style_readonly_field = true:warning

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="parentheses"></a>Предпочтения относительно круглых скобок

Правила стилей в этом разделе относятся к предпочтениям относительно круглых скобок, включая использование круглых скобок для арифметических, реляционных и других бинарных операторов.

В следующей таблице указаны имена и идентификаторы правил, применяемые языки программирования, значения по умолчанию и первая поддерживаемая версия Visual Studio:

| Имя правила | Идентификатор правила | Применимые языки | Значение по умолчанию в Visual Studio | Версия Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_parentheses_in_arithmetic_binary_operators | IDE0047 | C# и Visual Basic | always_for_clarity:silent | 15.8 |
| dotnet_style_parentheses_in_relational_binary_operators | IDE0047 | C# и Visual Basic | always_for_clarity:silent | 15.8 |
| dotnet_style_parentheses_in_other_binary_operators | IDE0047 | C# и Visual Basic | always_for_clarity:silent | 15.8 |
| dotnet_style_parentheses_in_other_operators | IDE0047 | C# и Visual Basic | never_if_unnecessary:silent | 15.8 |

**dotnet\_style\_parentheses\_in\_arithmetic\_binary_operators**

- Когда для этого правила установлено **always_for_clarity**, выбирайте скобки для указания приоритета арифметического оператора (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`).
- Когда для этого правила установлено **never_if_unnecessary**, не используйте круглые скобки, если приоритет арифметического оператора (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) очевиден.

Примеры кода:

```csharp
// dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
var v = a + (b * c);

// dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
var v = a + b * c;
```

```vb
' dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
Dim v = a + (b * c)

' dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
Dim v = a + b * c
```

**dotnet\_style\_parentheses\_in\_relational\_binary_operators**

- Когда для этого правила установлено **always_for_clarity**, выбирайте скобки, чтобы указать приоритет оператора отношений (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`).
- Когда для этого правила установлено **never_if_unnecessary**, не используйте круглые скобки, если приоритет оператора отношений (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) очевиден.

Примеры кода:

```csharp
// dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
var v = (a < b) == (c > d);

// dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
var v = a < b == c > d;
```

```vb
' dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
Dim v = (a < b) = (c > d)

' dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
Dim v = a < b = c > d
```

**dotnet\_style\_parentheses\_in\_other\_binary_operators**

- Когда для этого правила установлено **always_for_clarity**, выбирайте скобки для указания приоритета другого бинарного оператора (`&&`, `||`, `??`).
- Когда для этого правила установлено **never_if_unnecessary**, не используйте круглые скобки, если приоритет другого бинарного оператора (`&&`, `||`, `??`) очевиден.

Примеры кода:

```csharp
// dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
var v = a || (b && c);

// dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
var v = a || b && c;
```

```vb
' dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
Dim v = a OrElse (b AndAlso c)

' dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
Dim v = a OrElse b AndAlso c
```

**dotnet\_style\_parentheses\_in\_other_operators**

- Когда для этого правила установлено **always_for_clarity**, выбирайте скобки для указания приоритета оператора.
- Когда для этого правила установлено **never_if_unnecessary**, не используйте круглые скобки, если приоритет оператора очевиден.

Примеры кода:

```csharp
// dotnet_style_parentheses_in_other_operators = always_for_clarity
var v = (a.b).Length;

// dotnet_style_parentheses_in_other_operators = never_if_unnecessary
var v = a.b.Length;
```

```vb
' dotnet_style_parentheses_in_other_operators = always_for_clarity
Dim v = (a.b).Length

' dotnet_style_parentheses_in_other_operators = never_if_unnecessary
Dim v = a.b.Length
```

В файле *EDITORCONFIG* эти правила могут иметь следующий вид:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="expression_level"></a>Настройки уровня выражений

Правила стилей в этом разделе относятся к настройкам уровня выражений, включая использование инициализаторов объектов, инициализаторов наборов, явных или выводимых имен кортежей и выводимых анонимных типов.

В следующей таблице указаны имена и идентификаторы правил, применяемые языки программирования, значения по умолчанию и первая поддерживаемая версия Visual Studio:

| Имя правила | Идентификатор правила | Применимые языки | Значение по умолчанию в Visual Studio | Версия Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_object_initializer | IDE0017 | C# и Visual Basic | true:suggestion | Первый выпуск |
| dotnet_style_collection_initializer | IDE0028 | C# и Visual Basic | true:suggestion | Первый выпуск |
| dotnet_style_explicit_tuple_names | IDE0033 | C# 7.0+ и Visual Basic 15+ | true:suggestion | Первый выпуск |
| dotnet_style_prefer_inferred_tuple_names | IDE0037 | C# 7.1+ и Visual Basic 15+ | true:suggestion | 15,6 |
| dotnet_style_prefer_inferred_anonymous_type_member_names | IDE0037 | C# и Visual Basic | true:suggestion | 15,6 |
| dotnet_style_prefer_auto_properties | IDE0032 | C# и Visual Basic | true:silent | 15.7 |
| dotnet_style_prefer_is_null_check_over_reference_equality_method | IDE0041 | C# и Visual Basic | true:suggestion | 15.7 |
| dotnet_style_prefer_conditional_expression_over_assignment | IDE0045 | C# и Visual Basic | true:silent | 15.8 |
| dotnet_style_prefer_conditional_expression_over_return | IDE0046 | C# и Visual Basic | true:silent | 15.8 |

**dotnet\_style\_object_initializer**

- Когда для этого правила задано значение **true**, то предпочтительно инициализировать объекты с помощью инициализаторов объектов, когда это возможно.
- Когда для этого правила задано значение **false**, то предпочтительно *не* инициализировать объекты с помощью инициализаторов объектов.

Примеры кода:

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```

```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

**dotnet\_style\_collection_initializer**

- Когда для этого правила задано значение **true**, то предпочтительно инициализировать коллекции с помощью инициализаторов коллекций, когда это возможно.
- Когда для этого правила задано значение **false**, то предпочтительно *не* инициализировать коллекции с помощью инициализаторов коллекций.

Примеры кода:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```

```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```

**dotnet\_style\_explicit\_tuple_names**

- Когда для этого правила задано значение **true**, предпочтение отдается именам кортежей вместо свойств ItemX.
- Когда для этого правила задано значение **false**, предпочтение отдается свойствам ItemX вместо имен кортежей.

Примеры кода:

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```

```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

**dotnet\_style\_prefer\_inferred\_tuple_names**

- Если это правило имеет значение **true**, предпочтение отдается выводимым именам элементов кортежа.
- Если это правило имеет значение **true**, предпочтение отдается явным именам элементов кортежа.

Примеры кода:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

```vb
' dotnet_style_prefer_inferred_tuple_names = true
Dim tuple = (name, age)

' dotnet_style_prefer_inferred_tuple_names = false
Dim tuple = (name:=name, age:=age)
```

**dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names**

- Если это правило имеет значение **true**, предпочтение отдается выводимым именам автономных членов типа.
- Если это правило имеет значение **true**, предпочтение отдается явным именам автономных членов типа.

Примеры кода:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };
```

```vb
' dotnet_style_prefer_inferred_anonymous_type_member_names = true
Dim anon = New With {name, age}

' dotnet_style_prefer_inferred_anonymous_type_member_names = false
Dim anon = New With {.name = name, .age = age}
```

**dotnet\_style\_prefer\_auto\_properties**

- Если для этого правила задано значение **true**, автосвойства имеют приоритет перед другими свойствами с закрытыми резервными полями.
- Если для этого правила задано значение **false**, свойства с закрытыми резервными полями имеют приоритет перед автосвойствами.

Примеры кода:

```csharp
// dotnet_style_prefer_auto_properties = true
private int Age { get; }

// dotnet_style_prefer_auto_properties = false
private int age;

public int Age
{
    get
    {
        return age;
    }
}
```

```vb
' dotnet_style_prefer_auto_properties = true
Public ReadOnly Property Age As Integer

' dotnet_style_prefer_auto_properties = false
Private _age As Integer

Public ReadOnly Property Age As Integer
    Get
        return _age
    End Get
End Property
```

**dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method**

- Если для этого правила задано значение **true**, проверка значений null с сопоставлением шаблонов имеет приоритет перед object.ReferenceEquals.
- Если для этого правила задано значение **false**, object.ReferenceEquals имеет приоритет перед проверкой значений null с сопоставлением шаблонов.

Примеры кода:

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```

**dotnet\_style\_prefer\_conditional\_expression\_over_assignment**

- Если это правило имеет значение **true**, предпочтение отдается назначениям с тернарным условием вместо оператора if-else.
- Если это правило имеет значение **false**, предпочтение отдается назначениям с оператором if-else, а не тернарному условию.

Примеры кода:

```csharp
// dotnet_style_prefer_conditional_expression_over_assignment = true
string s = expr ? "hello" : "world";

// dotnet_style_prefer_conditional_expression_over_assignment = false
string s;
if (expr)
{
    s = "hello";
}
else
{
    s = "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_assignment = true
Dim s As String = If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_assignment = false
Dim s As String
If expr Then
    s = "hello"
Else
    s = "world"
End If
```

**dotnet\_style\_prefer\_conditional\_expression\_over_return**

- Если это правило имеет значение **true**, предпочтение отдается операторам return для использования тернарного условия вместо оператора if-else.
- Если это правило имеет значение **false**, предпочтение отдается операторам return для использования оператора if-else, а не тернарному условию.

Примеры кода:

```csharp
// dotnet_style_prefer_conditional_expression_over_return = true
return expr ? "hello" : "world"

// dotnet_style_prefer_conditional_expression_over_return = false
if (expr)
{
    return "hello";
}
else
{
    return "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_return = true
Return If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_return = false
If expr Then
    Return "hello"
Else
    Return "world"
End If
```

В файле *EDITORCONFIG* эти правила могут иметь следующий вид:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
```

#### <a name="null_checking"></a>Параметры проверки NULL

Правила стилей в этом разделе относятся к параметрам проверки NULL.

В следующей таблице указаны имена и идентификаторы правил, применяемые языки программирования, значения по умолчанию и первая поддерживаемая версия Visual Studio:

| Имя правила | Идентификатор правила | Применимые языки | Значение по умолчанию в Visual Studio | Версия Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_coalesce_expression | IDE0029 | C# и Visual Basic | true:suggestion | Первый выпуск |
| dotnet_style_null_propagation | IDE0031 | C# 6.0+ и Visual Basic 14+ | true:suggestion | Первый выпуск |

**dotnet\_style\_coalesce_expression**

- Когда для этого правила задано значение **true**, предпочтение отдается выражениям объединения со значением Null вместо проверки тернарного оператора.
- Когда для этого правила задано значение **false**, предпочтение отдается проверке тернарного оператора вместо выражений объединения со значением Null.

Примеры кода:

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```

```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

**dotnet\_style\_null_propagation**

- Когда для этого правила задано значение **true**, предпочтение отдается использованию условного оператора со значением Null, где это возможно.
- Когда для этого правила задано значение **false**, предпочтение отдается проверке тернарного оператора, где это возможно.

Примеры кода:

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```

```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```

В файле *EDITORCONFIG* эти правила могут иметь следующий вид:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

### <a name="c-code-style-settings"></a>Параметры стиля кода C#

Правила стилей в этом разделе относятся только к C#.

#### <a name="implicit-and-explicit-types"></a>Неявные и явные типы

Правила стилей в этом разделе (идентификаторы правил IDE0007 и IDE0008) относятся к использованию ключевого слова [var](/dotnet/csharp/language-reference/keywords/var) или явного типа в объявлении переменной. Это правило можно отдельно применять для встроенных типов, если этот тип является очевидным, а также в других местах.

В следующей таблице указаны имена правил, применяемые языки программирования и значения по умолчанию:

| Имя правила | Применимые языки | Значение по умолчанию в Visual Studio |
| ----------- | -------------------- | ----------------------|
| csharp_style_var_for_built_in_types | C# | true:silent |
| csharp_style_var_when_type_is_apparent | C# | true:silent |
| csharp_style_var_elsewhere | C# | true:silent |

**csharp\_style\_var\_for\_built\_in_types**

- Если это правило имеет значение **true**, предпочтение отдается использованию `var` для объявления переменных со встроенными системными типами, такими как `int`.
- Если это правило имеет значение **false**, для объявления переменных со встроенными системными типами, такими как `int`, предпочтение отдается явному типу, а не `var`.

Примеры кода:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

**csharp\_style\_var\_when\_type\_is_apparent**

- Когда это правило имеет значение **true**, предпочтение отдается `var`, если тип уже упоминается в правой части выражения объявления.
- Когда это правило имеет значение **false**, предпочтение отдается явному типу, а не `var`, если тип уже упоминается в правой части выражения объявления.

Примеры кода:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

**csharp\_style\_var_elsewhere**

- Когда это правило имеет значение **true**, предпочтение отдается `var`, а не явному типу во всех случаях, если только не переопределено другим правилом стиля кода.
- Когда это правило имеет значение **false**, предпочтение отдается явному типу, а не `var` во всех случаях, если только не переопределено другим правилом стиля кода.

Примеры кода:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="expression_bodied_members"></a>Элементы, воплощающие выражение

Правила стилей в этом разделе относятся к использованию [элементов, воплощающих выражение](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members), когда логика состоит из одного выражения. Это правило может применяться к методам, конструкторам, операторам, свойствам, индексаторам и методам доступа.

В следующей таблице указаны имена и идентификаторы правил, применяемые версии языков, значения по умолчанию и первая поддерживаемая версия Visual Studio:

| Имя правила | Идентификатор правила | Применимые языки | Значение по умолчанию в Visual Studio | Версия Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_style_expression_bodied_methods | IDE0022 | C# 6.0+ | false:silent | 15.3 |
| csharp_style_expression_bodied_constructors | IDE0021 | C# 7.0+ | false:silent | 15.3 |
| csharp_style_expression_bodied_operators | IDE0023 и IDE0024 | C# 7.0+ | false:silent | 15.3 |
| csharp_style_expression_bodied_properties | IDE0025 | C# 7.0+ | true:silent | 15.3 |
| csharp_style_expression_bodied_indexers | IDE0026 | C# 7.0+ | true:silent | 15.3 |
| csharp_style_expression_bodied_accessors | IDE0027 | C# 7.0+ | true:silent | 15.3 |

**csharp\_style\_expression\_bodied_methods**

Это правило принимает значения, описанные в следующей таблице:

| Значение | Описание |
| ----- |:----------- |
| true | Предпочитать элементы, воплощающие выражение, для методов |
| when_on_single_line | Предпочитать элементы, воплощающие выражение, для методов, если они будут находиться на одной строке |
| False | Предпочитать тела блоков для методов |

Примеры кода:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

**csharp\_style\_expression\_bodied_constructors**

Это правило принимает значения, описанные в следующей таблице:

| Значение | Описание |
| ----- |:----------- |
| true | Предпочитать элементы, воплощающие выражение, для конструкторов |
| when_on_single_line | Предпочитать элементы, воплощающие выражение, для конструкторов, если они будут находиться на одной строке |
| False | Предпочитать тела блоков для конструкторов |

Примеры кода:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

**csharp\_style\_expression\_bodied_operators**

Это правило принимает значения, описанные в следующей таблице:

| Значение | Описание |
| ----- |:----------- |
| true | Предпочитать элементы, воплощающие выражение, для операторов |
| when_on_single_line | Предпочитать элементы, воплощающие выражение, для операторов, если они будут находиться на одной строке |
| False | Предпочитать тела блоков для операторов |

Примеры кода:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

**csharp\_style\_expression\_bodied_properties**

Это правило принимает значения, описанные в следующей таблице:

| Значение | Описание |
| ----- |:----------- |
| true | Предпочитать элементы, воплощающие выражение, для свойств |
| when_on_single_line | Предпочитать элементы, воплощающие выражение, для свойств, если они будут находиться на одной строке |
| False | Предпочитать тела блоков для свойств |

Примеры кода:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

**csharp\_style\_expression\_bodied_indexers**

Это правило принимает значения, описанные в следующей таблице:

| Значение | Описание |
| ----- |:----------- |
| true | Предпочитать элементы, воплощающие выражение, для индексаторов |
| when_on_single_line | Предпочитать элементы, воплощающие выражение, для индексаторов, если они будут находиться на одной строке |
| False | Предпочитать тела блоков для индексаторов |

Примеры кода:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

**csharp\_style\_expression\_bodied_accessors**

Это правило принимает значения, описанные в следующей таблице:

| Значение | Описание |
| ----- |:----------- |
| true | Предпочитать элементы, воплощающие выражение, для методов доступа |
| when_on_single_line | Предпочитать элементы, воплощающие выражение, для методов доступа, если они будут находиться на одной строке |
| False | Предпочитать тела блоков для методов доступа |

Примеры кода:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
```

#### <a name="pattern_matching"></a>Сопоставление шаблонов

Правила стилей в этом разделе относятся к использованию [сопоставления шаблонов](/dotnet/csharp/pattern-matching) в C#.

В следующей таблице указаны имена и идентификаторы правил, применяемые версии языков и значения по умолчанию:

| Имя правила | Идентификатор правила | Применимые языки | Значение по умолчанию в Visual Studio |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_pattern_matching_over_is_with_cast_check | IDE0020 | C# 7.0+ | true:suggestion |
| csharp_style_pattern_matching_over_as_with_null_check | IDE0019 | C# 7.0+ | true:suggestion |

**csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check**

- Когда для этого правила задано значение **true**, то предпочтительно использовать сопоставления шаблонов вместо выражений `is` с приведениями типов.
- Когда для этого правила задано значение **false**, то предпочтительно использовать выражения `is` с приведениями типов вместо сопоставления шаблонов.

Примеры кода:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

**csharp\_style\_pattern\_matching\_over\_as\_with\_null_check**

- Когда для этого правила задано значение **true**, то предпочтительно использовать сопоставление шаблонов вместо выражений `as` с проверками Null, чтобы определить, имеет ли что-то определенный тип.
- Когда для этого правила задано значение **false**, то предпочтительно использовать выражения `as` с проверками Null вместо соответствия шаблонам, чтобы определить, имеет ли что-то определенный тип.

Примеры кода:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="inlined_variable_declarations"></a>Встроенные объявления переменных

Это правило стиля определяет, объявляются ли переменные `out` встроенным образом или нет. Начиная с версии 7 языка C# [переменную out можно объявлять в списке аргументов вызова метода](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), а не отдельно.

В следующей таблице указаны имена и идентификаторы правил, применяемые версии языков и значения по умолчанию:

| Имя правила | Идентификатор правила | Применимые языки | Значение по умолчанию в Visual Studio |
| --------- | -------- | -------------------- | ----------------------|
| csharp_style_inlined_variable_declaration | IDE0018 | C# 7.0+ | true:suggestion |

**csharp\_style\_inlined\_variable_declaration**

- Когда для этого правила задано значение **true**, то предпочтительно объявлять переменные `out` встроенным образом в списке аргументов вызова метода, если это возможно.
- Когда для этого правила задано значение **false**, то предпочтительно объявлять переменные `out` до вызова метода.

Примеры кода:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

#### <a name="expression_level_csharp"></a>Настройки уровня выражений

В этом разделе описываются правила стиля, относящиеся к предпочтениям на уровне выражений, включая использование [выражений по умолчанию](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), деконструированные переменные и предпочтение локальных функций анонимным.

В следующей таблице указаны имена и идентификаторы правил, применяемые версии языков, значения по умолчанию и первая поддерживаемая версия Visual Studio:

| Имя правила | Идентификатор правила | Применимые языки | Значение по умолчанию в Visual Studio | Версия Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_simple_default_expression | IDE0034 | C# 7.1+ | true:suggestion | 15.3 |
| csharp_style_deconstructed_variable_declaration | IDE0042 | C# 7.0+ | true:suggestion | 15.5 |
| csharp_style_pattern_local_over_anonymous_function | IDE0039 | C# 7.0+ | true:suggestion | 15.5 |

**csharp\_prefer\_simple\_default_expression**

Это правило стиля определяет использование [литерала `default` для выражений значения по умолчанию](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), если компилятор может вывести тип выражения.

- Когда для этого правила задано значение **true**, предпочтение отдается `default` вместо `default(T)`.
- Когда для этого правила задано значение **false**, предпочтение отдается `default(T)` вместо `default`.

Примеры кода:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

**csharp\_style\_deconstructed\_variable_declaration**

- Если этому правилу присвоено значение **true**, предпочитать объявление деконструированной переменной.
- Если этому правилу присвоено значение **false**, не предпочитать объявление деконструированной переменной.

Примеры кода:

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

**csharp\_style\_pattern\_local\_over\_anonymous_function**

- Если этому правилу присвоено значение **true**, предпочитать локальные функции анонимным.
- Если этому правилу присвоено значение **false**, предпочитать анонимные функции локальным.

Примеры кода:

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
```

#### <a name="null_checking_csharp"></a>Настройки проверки Null

Эти правила стиля определяют синтаксис, связанный с проверкой `null`, включая использование выражений `throw` или операторов `throw`, а также выбор между проверкой Null и использованием условного оператора объединения (`?.`) при вызове [лямбда-выражения](/dotnet/csharp/lambda-expressions).

В следующей таблице указаны имена и идентификаторы правил, применяемые версии языков и значения по умолчанию:

| Имя правила | Идентификатор правила | Применимые языки | Значение по умолчанию в Visual Studio |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_throw_expression | IDE0016 | C# 7.0+ | true:suggestion |
| csharp_style_conditional_delegate_call | IDE0041 | C# 6.0+ | true:suggestion |

**csharp\_style\_throw_expression**

- Когда для этого правила задано значение **true**, то предпочтительно использовать выражения `throw` вместо операторов `throw`.
- Когда для этого правила задано значение **false**, то предпочтительно использовать операторы `throw` вместо выражений `throw`.

Примеры кода:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

**csharp\_style\_conditional\_delegate_call**

- Когда для этого правила задано значение **true**, то предпочтительно использовать условный оператор объединения (`?.`) при вызове лямбда-выражения вместо выполнения проверки Null.
- Когда для этого правила задано значение **false**, то предпочтительно выполнять проверку значения Null перед вызовом лямбда-выражения вместо использования условного оператора объединения (`?.`).

Примеры кода:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="code_block"></a>Настройки блока кода

Это правило стиля определяет использование фигурных скобок `{ }` вокруг блоков кода.

В следующей таблице указаны имена и идентификаторы правил, применяемые версии языков, значения по умолчанию и первая поддерживаемая версия Visual Studio:

| Имя правила | Идентификатор правила | Применимые языки | Значение по умолчанию в Visual Studio | Версия Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_braces | IDE0011 | C# | true:silent | 15.3 |

**csharp\_prefer\_braces**

- Когда для этого правила задано значение **true**, то предпочтительно использовать фигурные скобки даже для одной строки кода.
- Когда для этого правила задано значение **false**, то предпочтительно не использовать фигурные скобки, если это допустимо.

Примеры кода:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

## <a name="formatting-conventions"></a>Соглашения по форматированию

Большинство правил для соглашений по форматированию имеет следующий формат:

`rule_name = false|true`

Вы указываете значение **true** (предпочитать этот стиль) или **false** (не предпочитать этот стиль). Уровень серьезности указывать не нужно. Для нескольких правил вместо true или false указываются другие значения, описывающие, когда и где нужно применить такое правило.

Следующий список содержит правила для соглашений по форматированию, доступные в Visual Studio:

- Параметры форматирования .NET
    - [Управление директивами using](#usings)
        - dotnet_sort_system_directives_first
        - dotnet_separate_import_directive_groups
- Параметры форматирования C#
    - [Параметры перевода строки](#newline)
        - csharp_new_line_before_open_brace
        - csharp_new_line_before_else
        - csharp_new_line_before_catch
        - csharp_new_line_before_finally
        - csharp_new_line_before_members_in_object_initializers
        - csharp_new_line_before_members_in_anonymous_types
        - csharp_new_line_between_query_expression_clauses
    - [Параметры отступа](#indent)
        - csharp_indent_case_contents
        - csharp_indent_switch_labels
        - csharp_indent_labels
    - [Параметры интервалов](#spacing)
        - csharp_space_after_cast
        - csharp_space_after_keywords_in_control_flow_statements
        - csharp_space_between_method_declaration_parameter_list_parentheses
        - csharp_space_between_method_call_parameter_list_parentheses
        - csharp_space_between_parentheses
        - csharp_space_before_colon_in_inheritance_clause
        - csharp_space_after_colon_in_inheritance_clause
        - csharp_space_around_binary_operators
        - csharp_space_between_method_declaration_empty_parameter_list_parentheses
        - csharp_space_between_method_call_name_and_opening_parenthesis
        - csharp_space_between_method_call_empty_parameter_list_parentheses
    - [Параметры переноса](#wrapping)
        - csharp_preserve_single_line_statements
        - csharp_preserve_single_line_blocks

### <a name="net-formatting-settings"></a>Параметры форматирования .NET

Правила форматирования в этом разделе относятся как к C#, так и к Visual Basic.

#### <a name="usings"></a>Управление директивами using

Это правило форматирования описывает размещение директив using System.* по отношению к другим директивам using.

В следующей таблице указаны имена правил, применяемые языки, значения по умолчанию и первая поддерживаемая версия Visual Studio:

| Имя правила | Применимые языки | Значение по умолчанию в Visual Studio | Версия Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| dotnet_sort_system_directives_first | C# и Visual Basic | true | 15.3 |
| dotnet_separate_import_directive_groups | C# и Visual Basic | False | 15.5 |

**dotnet\_sort\_system\_directives_first**

- Когда для этого правила задано значение **true**, то предпочтительно сортировать директивы using System.* в алфавитном порядке, располагая их перед всеми остальными директивами using.
- Когда для этого правила задано значение **false**, не располагайте директивы using System.* перед другими директивами using.

Примеры кода:

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

Пример файла *EDITORCONFIG*:

```ini
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
```

**dotnet\_separate\_import\_directive\_groups**

- Если это правило имеет значение **true**, поместите пустую строку между группами директив using.
- Если это правило имеет значение **false**, не помещайте пустую строку между группами директив using.

Примеры кода:

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

Пример файла *EDITORCONFIG*:

```ini
# .NET formatting settings:
[*.{cs,vb}]
dotnet_separate_import_directive_groups = true
```

### <a name="c-formatting-settings"></a>Параметры форматирования C#

Правила форматирования в этом разделе относятся только к коду C#.

#### <a name="newline"></a>Параметры перевода строки

Эти правила форматирования относятся использованию новых строк для форматирования кода.

В следующей таблице указаны имена правил для новых строк, применяемые языки, значения по умолчанию и первая поддерживаемая версия Visual Studio:

| Имя правила | Применимые языки | Значение по умолчанию в Visual Studio | Версия Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_new_line_before_open_brace | C# | все | 15.3 |
| csharp_new_line_before_else | C# | true | 15.3 |
| csharp_new_line_before_catch | C# | true | 15.3 |
| csharp_new_line_before_finally | C# | true | 15.3 |
| csharp_new_line_before_members_in_object_initializers | C# | true | 15.3 |
| csharp_new_line_before_members_in_anonymous_types | C# | true | 15.3 |
| csharp_new_line_between_query_expression_clauses | C# | true | 15.3 |

**csharp\_new\_line\_before\_open_brace**

Это правило определяет, следует ли располагать открывающую фигурную скобку `{` одной строке с предшествующим кодом или на новой строке. Для этого правила не нужно указывать значение **true** или **false**. Вместо этого укажите **all**, **none** либо один или несколько элементов кода, таких как **methods** или **properties**, чтобы определить, когда следует применять это правило. Все допустимые значения перечислены в следующей таблице:

| Значение | Описание
| ------------- |:-------------|
| accessors, anonymous_methods, anonymous_types, control_blocks, events, indexers, lambdas, local_functions, methods, object_collection_array_initializers, properties, types.<br>(При использовании нескольких значений разделяйте их с помощью ",".) | Требовать, чтобы фигурные скобки для указанных элементов кода размещались в новой строке (стиль Олмана). |
| все | Требовать, чтобы фигурные скобки для всех выражений размещались в новой строке (стиль Олмана). |
| Нет | Требовать, чтобы фигурные скобки для всех выражений размещались в строке выражения (стиль Кернигана и Ритчи). |

Примеры кода:

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

**csharp\_new\_line\_before_else**

- Когда для этого правила задано значение **true**, размещайте операторы `else` в новой строке.
- Когда для этого правила задано значение **false**, размещайте операторы `else` в той же строке.

Примеры кода:

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

**csharp\_new\_line\_before_catch**

- Когда для этого правила задано значение **true**, размещайте операторы `catch` в новой строке.
- Когда для этого правила задано значение **false**, размещайте операторы `catch` в той же строке.

Примеры кода:

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

**csharp\_new\_line\_before_finally**

- Когда для этого правила задано значение **true**, инструкции `finally` нужно размещать в новой строке после закрывающей фигурной скобки.
- Когда для этого правила задано значение **false**, инструкции `finally` нужно размещать в одной строке с закрывающей фигурной скобкой.

Примеры кода:

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

**csharp\_new\_line\_before\_members\_in\_object_initializers**

- Если для этого правила задано значение **true**, требуется, чтобы элементы инициализаторов объектов размещались в разных строках.
- Когда для этого правила задано значение **false**, требуется, чтобы элементы инициализаторов объектов размещались в одной строке.

Примеры кода:

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

**csharp\_new\_line\_before\_members\_in\_anonymous_types**

- Когда для этого правила задано значение **true**, требуется, чтобы элементы анонимных типов размещались в разных строках.
- Когда для этого правила задано значение **false**, требуется, чтобы элементы анонимных типов размещались в одной строке.

Примеры кода:

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

**csharp_new_line_between_query_expression_clauses**

- Когда для этого правила задано значение **true**, требуется, чтобы элементы в предложениях выражений запросов размещались в разных строках.
- Когда для этого правила задано значение **false**, требуется, чтобы элементы в предложениях выражений запросов размещались в одной строке.

Примеры кода:

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

Пример файла *EDITORCONFIG*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="indent"></a>Параметры отступа

Эти правила форматирования относятся к использованию отступа для форматирования кода.

В следующей таблице указаны имена правил, применяемые языки, значения по умолчанию и первая поддерживаемая версия Visual Studio:

| Имя правила | Применимые языки | Значение по умолчанию в Visual Studio | Версия Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_indent_case_contents | C# | true | 15.3 |
| csharp_indent_switch_labels | C# | true | 15.3 |
| csharp_indent_labels | C# | no_change | 15.3 |

**csharp\_indent\_case_contents**

- Когда для этого правила задано значение **true**, нужно сделать отступ для конструкции case `switch`.
- Когда для этого правила задано значение **false**, делать отступ для конструкции case `switch` не нужно.

Примеры кода:

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent\_switch_labels**

- Когда для этого правила задано значение **true**, нужно сделать отступ для меток `switch`.
- Когда для этого правила задано значение **false**, делать отступ для меток `switch` не нужно.

Примеры кода:

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent_labels**

Это правило принимает не значение **true** или **false**, а одно из следующих значений:

| Значение | Описание |
| ----- |:----------- |
| flush_left | Метки размещаются в крайнем левом столбце |
| one_less_than_current | Метки размещаются на предыдущей позиции отступа относительно текущего контекста |
| no_change | Метки размещаются на той же позиции отступа, что и текущий контекст |

Примеры кода:

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

Пример файла *EDITORCONFIG*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="spacing"></a>Параметры интервалов

Эти правила форматирования относятся к использованию пробелов для форматирования кода.

В следующей таблице указаны имена правил, применяемые языки, значения по умолчанию и первая поддерживаемая версия Visual Studio:

| Имя правила | Применимые языки | Значение по умолчанию в Visual Studio | Версия Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_space_after_cast | C# | False | 15.3 |
| csharp_space_after_keywords_in_control_flow_statements | C# | true | 15.3 |
| csharp_space_between_method_declaration_parameter_list_parentheses | C# | False | 15.3 |
| csharp_space_between_method_call_parameter_list_parentheses | C# | False | 15.3 |
| csharp_space_between_parentheses | C# | False | 15.3 |
| csharp_space_before_colon_in_inheritance_clause | C# | true | 15.7 |
| csharp_space_after_colon_in_inheritance_clause | C# | true | 15.7 |
| csharp_space_around_binary_operators | C# | before_and_after | 15.7 |
| csharp_space_between_method_declaration_empty_parameter_list_parentheses | C# | False | 15.7 |
| csharp_space_between_method_call_name_and_opening_parenthesis | C# | False | 15.7 |
| csharp_space_between_method_call_empty_parameter_list_parentheses | C# | False | 15.7 |

**csharp\_space\_after_cast**

- Когда для этого правила задано значение **true**, требуется наличие пробела между типом и значением в приведении.
- Когда для этого правила задано значение **false**, требуется _отсутствие_ пробела между типом и значением в приведении.

Примеры кода:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

**csharp_space_after_keywords_in_control_flow_statements**

- Когда для этого правила задано значение **true**, требуется наличие пробела после ключевого слова в операторе потока управления, например цикле `for`.
- Когда для этого правила задано значение **false**, требуется _отсутствие_ пробела после ключевого слова в операторе потока управления, например цикле `for`.

Примеры кода:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

**csharp_space_between_method_declaration_parameter_list_parentheses**

- Когда для этого правила задано значение **true**, нужно поставить пробел после открывающей скобки и перед закрывающей скобкой в списке параметров объявления метода.
- Когда для этого правила задано значение **false**, ставить пробел после открывающей скобки и перед закрывающей скобкой в списке параметров объявления метода не нужно.

Примеры кода:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

**csharp_space_between_method_call_parameter_list_parentheses**

- Когда для этого правила задано значение **true**, нужно поставить пробел после открывающей скобки и перед закрывающей скобкой в вызове метода.
- Когда для этого правила задано значение **false**, ставить пробел после открывающей скобки и перед закрывающей скобкой в вызове метода не нужно.

Примеры кода:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

**csharp_space_between_parentheses**

Это правило принимает одно или несколько значений из следующей таблицы:

| Значение | Описание |
| ----- |:------------|
| control_flow_statements | Добавлять пробел между скобками для операторов потока управления |
| выражения | Добавлять пробел между скобками для выражений |
| type_casts | Размещать пробел между скобками в приведениях типов |

Если пропустить это правило или использовать значение, отличное от `control_flow_statements`, `expressions` или `type_casts`, этот параметр не применяется.

Примеры кода:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

**csharp\_space\_before\_colon\_in\_inheritance_clause**

- Если для этого правила задано значение **true**, обязательно наличие пробела перед двоеточием для баз или интерфейсов в объявлении типа.
- Если для этого правила задано значение **false**, обязательно _отсутствие_ пробела перед двоеточием для баз или интерфейсов в объявлении типа.

Примеры кода:

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

**csharp\_space\_after\_colon\_in\_inheritance_clause**

- Если для этого правила задано значение **true**, обязательно наличие пробела после двоеточия для баз или интерфейсов в объявлении типа.
- Если для этого правила задано значение **false**, обязательно _отсутствие_ пробела после двоеточия для баз или интерфейсов в объявлении типа.

Примеры кода:

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

**csharp\_space\_around\_binary_operators**

Это правило принимает одно из значений, описанных в следующей таблице.

| Значение | Описание |
| ----- |:------------|
| before_and_after | Вставлять пробел до и после бинарных операторов |
| Нет | Удалять пробелы до и после бинарных операторов |
| игнорировать | Игнорировать пробелы вокруг бинарных операторов |

Если пропустить это правило или использовать значение, отличное от `before_and_after`, `none` или `ignore`, этот параметр не применяется.

Примеры кода:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

**csharp_space_between_method_declaration_empty_parameter_list_parentheses**

- Если для этого правила задано значение **true**, необходимо вставлять пробел между скобками пустого списка параметров при объявлении метода.
- Если для этого правила задано значение **false**, необходимо удалить пробел между скобками пустого списка параметров при объявлении метода.

Примеры кода:

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_name_and_opening_parenthesis**

- Если для этого правила задано значение **true**, необходимо вставлять пробел между именем вызываемого метода и открывающей скобкой.
- Если для этого правила задано значение **false**, необходимо удалить пробел между именем вызываемого метода и открывающей скобкой.

Примеры кода:

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_empty_parameter_list_parentheses**

- Если для этого правила задано значение **true**, необходимо вставлять пробел между скобками пустого списка аргументов.
- Если для этого правила задано значение **false**, необходимо удалить пробел между скобками пустого списка аргументов.

Примеры кода:

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

Пример файла *EDITORCONFIG*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
```

#### <a name="wrapping"></a>Параметры переноса

Эти правила форматирования определяют размещение операторов и блоков кода в одной или разных строках.

В следующей таблице указаны имена правил, применяемые языки, значения по умолчанию и первая поддерживаемая версия Visual Studio:

| Имя правила | Применимые языки | Значение по умолчанию в Visual Studio | Версия Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_preserve_single_line_statements | C# | true | 15.3 |
| csharp_preserve_single_line_blocks | C# | true | 15.3 |

**csharp_preserve_single_line_statements**

- Когда для этого правила задано значение **true**, то нужно оставлять выражения и объявления элемента в одной строке.
- Когда для этого правила задано значение **false**, то нужно оставлять выражения и объявления элемента в разных строках.

Примеры кода:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

**csharp_preserve_single_line_blocks**

- Когда для этого правила задано значение **true**, то нужно оставлять блок кода в одной строке.
- Когда для этого правила задано значение **false**, то нужно оставлять блок кода в разных строках.

Примеры кода:

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

Пример файла *EDITORCONFIG*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

## <a name="example-editorconfig-file"></a>Пример файла EditorConfig

Чтобы помочь вам приступить к работе, ниже приведен пример файла *.editorconfig* с параметрами по умолчанию.

```ini
###############################
# Core EditorConfig Options   #
###############################

root = true

# All files
[*]
indent_style = space

# Code files
[*.{cs,csx,vb,vbx}]
indent_size = 4
insert_final_newline = true
charset = utf-8-bom

###############################
# .NET Coding Conventions     #
###############################

[*.{cs,vb}]
# Organize usings
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = false

# this. preferences
dotnet_style_qualification_for_field = false:silent
dotnet_style_qualification_for_property = false:silent
dotnet_style_qualification_for_method = false:silent
dotnet_style_qualification_for_event = false:silent

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:silent
dotnet_style_predefined_type_for_member_access = true:silent

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:silent
dotnet_style_readonly_field = true:suggestion

# Expression-level preferences
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent

###############################
# Naming Conventions          #
###############################

# Style Definitions
dotnet_naming_style.pascal_case_style.capitalization             = pascal_case

# Use PascalCase for constant fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.constant_fields_should_be_pascal_case.symbols  = constant_fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.style    = pascal_case_style
dotnet_naming_symbols.constant_fields.applicable_kinds            = field
dotnet_naming_symbols.constant_fields.applicable_accessibilities  = *
dotnet_naming_symbols.constant_fields.required_modifiers          = const

###############################
# C# Code Style Rules         #
###############################

[*.cs]
# var preferences
csharp_style_var_for_built_in_types = true:silent
csharp_style_var_when_type_is_apparent = true:silent
csharp_style_var_elsewhere = true:silent

# Expression-bodied members
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:silent
csharp_style_expression_bodied_indexers = true:silent
csharp_style_expression_bodied_accessors = true:silent

# Pattern-matching preferences
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion

# Null-checking preferences
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Expression-level preferences
csharp_prefer_braces = true:silent
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion

###############################
# C# Formatting Rules         #
###############################

# New line preferences
csharp_new_line_before_open_brace = all
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left

# Space preferences
csharp_space_after_cast = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false

# Wrapping preferences
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true

##################################
# Visual Basic Code Style Rules  #
##################################

[*.vb]
# Modifier preferences
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

## <a name="see-also"></a>См. также

- [Быстрые действия](../ide/quick-actions.md)
- [Соглашения об именовании в среде .NET для EditorConfig](../ide/editorconfig-naming-conventions.md)
- [Создание переносимых, настраиваемых параметров редактора](../ide/create-portable-custom-editor-options.md)
- [Файл EDITORCONFIG для платформы компиляторов .NET](https://github.com/dotnet/roslyn/blob/master/.editorconfig).
