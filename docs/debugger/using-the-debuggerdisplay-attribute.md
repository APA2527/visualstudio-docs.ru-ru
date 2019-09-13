---
title: Отображение пользовательских сведений с помощью DebuggerDisplay | Документация Майкрософт
ms.date: 01/09/2019
ms.topic: conceptual
helpviewer_keywords:
- attributes, debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fbe3ff31d00945ef462c5c20eb1c4b33c250f97
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887749"
---
# <a name="tell-the-debugger-what-to-show-using-the-debuggerdisplay-attribute-c-visual-basic-f-ccli"></a>Сообщить отладчику, что отображать с помощью атрибута DebuggerDisplay (C#, Visual Basic, F# C++/CLI)
<xref:System.Diagnostics.DebuggerDisplayAttribute> управляет тем, как объект, свойство или поле отображаются в окнах переменных отладчика. Этот атрибут можно применять для типов, делегатов, свойств, полей и сборок. Если применяется к базовому типу, атрибут также применяется к подклассу.

Атрибут `DebuggerDisplay` имеет один аргумент, определяющий строку, которая должна отображаться в столбце "Значение" для экземпляров типа. Эта строка может содержать фигурные скобки (`{` и `}`). Текст, заключенный в фигурные скобки, вычисляется как поле, свойство или метод.

Если класс содержит переопределенный метод `ToString()` , отладчик использует этот метод вместо значения по умолчанию `{<typeName>}`. Таким образом, если имеется переопределенный метод `ToString()` , отладчик использует его вместо значения по умолчанию`{<typeName>}`и нет необходимости использовать `DebuggerDisplay`. Если используется и то и другое, то атрибут `DebuggerDisplay` будет иметь более высокий приоритет по отношению к переопределенному методу `ToString()`. Атрибут также имеет приоритет над переопределенным `ToString()` методом в подклассе. `DebuggerDisplay`

Будет ли отладчик выполнять неявный вызов метода `ToString()` , зависит от заданных пользователем параметров в диалоговом окне **Сервис &gt; Параметры &gt; Отладка** . В Visual Basic неявный вызов метода `ToString()` не производится.

> [!IMPORTANT]
> Если в диалоговом окне **Сервис &gt; Параметры &gt; Отладка** установлен флажок **Показывать базовую структуру объектов в окнах переменных** , то атрибут `DebuggerDisplay` игнорируется.

> [!NOTE]
> Для машинного кода этот атрибут поддерживается только в C++коде/CLI.

В следующей таблице показано несколько примеров возможного использования атрибута `DebuggerDisplay` для вывода строк удобочитаемого вида.

|Атрибут|Строка, выводимая в столбце "Значение"|
|---------------| - |
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> Применение для типа с полями `x` и `y`.|`x = 5 y = 18`|
|`[DebuggerDisplay("String value is {getString()}")]`Синтаксис параметра может различаться в зависимости от языка. Будьте внимательны при его использовании.|`String value is [5, 6, 6]`|

Атрибут`DebuggerDisplay` также может принимать именованные параметры.

|Параметры|Цель|
|----------------|-------------|
|`Name`, `Type`|Эти параметры влияют на столбцы **Имя** и **Тип** окон переменных. (Для них также может быть задан вывод строк с использованием того же синтаксиса, что и для конструктора.) Злоупотребление этими параметрами или их неправильное использование может, однако, привести к выводу неудобочитаемых или недостоверных данных.|
|`Target`, `TargetTypeName`|Указывает конечный тип, когда атрибут используется на уровне сборки.|

Файл autoexp.cs использует атрибут DebuggerDisplay на уровне сборки. Файл autoexp.cs определяет расширения по умолчанию, которые Visual Studio использует для объектов .NET. В файле autoexp.cs можно просмотреть примеры использования атрибута DebuggerDisplay. При необходимости в файл autoexp.cs можно внести изменения и скомпилировать его, чтобы изменить расширения по умолчанию. Прежде чем изменять файл autoexp.cs, следует обязательно сделать его резервную копию.

Чтобы создать файл autoexp.cs, откройте командную строку разработчика для VS 2015 и выполните следующие команды.

```cmd
cd <directory containing autoexp.cs>
csc /t:library autoexp.cs
```

Изменения в файле autoexp.dll будут учтены в следующем сеансе отладки.

## <a name="using-expressions-in-debuggerdisplay"></a>Использование выражений в атрибуте DebuggerDisplay
Хотя в атрибуте DebuggerDisplay допускается использовать общее выражение внутри фигурных скобок, делать это не рекомендуется.

Общее выражение внутри атрибута DebuggerDisplay имеет неявный доступ к указателю `this` только для текущего экземпляра конечного типа. Выражение не имеет доступа к псевдонимам, локальным переменным или указателям. Если выражение ссылается на свойства, то атрибуты для этих свойств не обрабатываются. Например, код C# `[DebuggerDisplay("Object {count - 2}")]` отобразил бы `Object 6`, если бы поле `count` имело значение 8.

Использование выражений в атрибуте DebuggerDisplay может привести к следующим проблемам:

- Вычисление выражений является наиболее ресурсоемкой операцией в отладчике, причем выражение вычисляется при каждом его отображении. Это может вызвать проблемы производительности при пошаговом выполнении кода. Например, сложное выражение, используемое для отображения значений в коллекции или в списке, при большом количестве элементов может вычисляться очень медленно.

- Выражения вычисляются с помощью вычислителя выражений языка текущего кадра стека, а не языка, на котором было написано выражение. Это может привести к непредсказуемым результатам, если языки различаются.

- Вычисление выражения может изменить состояние приложения. Например, выражение, которое задает значение свойства, изменяет значение свойства в выполняемом коде.

  Одним из способов сократить возможные проблемы вычисления выражения является создание закрытого свойства, которое выполняет операцию и возвращает строку. Атрибут DebuggerDisplay сможет отобразить значение этого закрытого свойства. Ниже показан пример реализации этого способа.

```csharp
[DebuggerDisplay("{DebuggerDisplay,nq}")]
public sealed class MyClass
{
    public int count { get; set; }
    public bool flag { get; set; }
    private string DebuggerDisplay
    {
        get
        {
            return string.Format("Object {0}", count - 2);
        }
    }
}
```

Суффикс ", НК" указывает средству оценки выражений удалить кавычки при отображении окончательного значения (НК = без кавычек).

## <a name="example"></a>Пример
Следующий пример демонстрирует способ использования атрибута `DebuggerDisplay`совместно с атрибутами `DebuggerBrowseable` и `DebuggerTypeProxy`. При работе данного кода в окна переменных отладчика, например в окно **Контрольные значения** , выводится расширенная информация, а именно:

|**Name**|**Значение**|**Type**|
|--------------|---------------|--------------|
|Ключ|"три"|object {string}|
|Значение|3|object {int}|

```csharp
[DebuggerDisplay("{value}", Name = "{key}")]
internal class KeyValuePairs
{
    private IDictionary dictionary;
    private object key;
    private object value;
    public KeyValuePairs(IDictionary dictionary, object key, object value)
    {
        this.value = value;
        this.key = key;
        this.dictionary = dictionary;
    }

    public object Key
    {
        get { return key; }
        set
        {
            object tempValue = dictionary[key];
            dictionary.Remove(key);
            key = value;
            dictionary.Add(key, tempValue);
        }
    }

    public object Value
    {
        get { return this.value; }
        set
        {
            this.value = value;
            dictionary[key] = this.value;
        }
    }
}

[DebuggerDisplay("{DebuggerDisplay,nq}")]
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable
{
    public Hashtable hashtable;

    public MyHashtable()
    {
        hashtable = new Hashtable();
    }

    private string DebuggerDisplay { get { return "Count = " + hashtable.Count; } }

    private class HashtableDebugView
    {
        private MyHashtable myhashtable;
        public HashtableDebugView(MyHashtable myhashtable)
        {
            this.myhashtable = myhashtable;
        }

        [DebuggerBrowsable(DebuggerBrowsableState.RootHidden)]
        public KeyValuePairs[] Keys
        {
            get
            {
                KeyValuePairs[] keys = new KeyValuePairs[myhashtable.hashtable.Count];

                int i = 0;
                foreach (object key in myhashtable.hashtable.Keys)
                {
                    keys[i] = new KeyValuePairs(myhashtable.hashtable, key, myhashtable.hashtable[key]);
                    i++;
                }
                return keys;
            }
        }
    }
}
```

## <a name="see-also"></a>См. также

- [Использование атрибута DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Создание настраиваемых представлений управляемых объектов](../debugger/create-custom-views-of-dot-managed-objects.md)
- [Определители формата в C#](../debugger/format-specifiers-in-csharp.md)
- [Повышение эффективности отладки с помощью атрибутов просмотра отладчика](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
