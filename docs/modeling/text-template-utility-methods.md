---
title: Служебные методы для текстовых шаблонов
description: Сведения о различных вспомогательных методах текстовых шаблонов, доступных при написании кода в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b0015e68f7d78c2b33eaeb9e0bfb404acaed834
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362019"
---
# <a name="text-template-utility-methods"></a>Служебные методы для текстовых шаблонов

Существует несколько методов, которые всегда доступны при написании кода в текстовом шаблоне Visual Studio. Эти методы определяются в <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

> [!TIP]
> Кроме того, можно использовать другие методы и службы, предоставляемые средой размещения, в обычном (не предварительно обработанном) текстовом шаблоне. Например, можно разрешить пути к файлам, вести журнал ошибок и получить службы, предоставляемые Visual Studio, и все загруженные пакеты. Дополнительные сведения см. в разделе [доступ к Visual Studio из текстового шаблона](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

## <a name="write-methods"></a>Методы записи

Можно использовать `Write()` `WriteLine()` методы и для добавления текста в стандартный блок кода вместо использования блока кода выражения. Следующие два блока кода функционально эквивалентны.

### <a name="code-block-with-an-expression-block"></a>Блок кода с блоком выражения

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>Блок кода с помощью метода WriteLine ()

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

Может оказаться полезным использовать один из этих служебных методов вместо блока выражения внутри длинного блока кода с вложенными структурами элементов управления.

`Write()`Методы и `WriteLine()` имеют две перегрузки, один из которых принимает один строковый параметр и один, принимающий строку составного формата плюс массив объектов для включения в строку (например, `Console.WriteLine()` метод). Следующие два применения `WriteLine()` функций функционально эквивалентны:

```
<#
    string msg = "Say: {0}, {1}, {2}";
    string s1 = "hello";
    string s2 = "goodbye";
    string s3 = "farewell";

    WriteLine(msg, s1, s2, s3);
    WriteLine("Say: hello, goodbye, farewell");
#>
```

## <a name="indentation-methods"></a>Методы отступов

Для форматирования выходных данных текстового шаблона можно использовать методы отступов. <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>Класс имеет `CurrentIndent` строковое свойство, которое показывает текущий отступ в текстовом шаблоне, и `indentLengths` поле, содержащее список добавленных отступов. Можно добавить отступ с помощью `PushIndent()` метода и вычесть отступ с помощью `PopIndent()` метода. Если необходимо удалить все отступы, используйте `ClearIndent()` метод. В следующем блоке кода показано использование следующих методов:

```
<#
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    ClearIndent();
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
#>
```

Этот блок кода создает следующие выходные данные:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Методы error и Warning

Для добавления сообщений в Список ошибок Visual Studio можно использовать служебные методы ошибок и предупреждений. Например, следующий код добавит сообщение об ошибке в Список ошибок.

```
<#
  try
  {
    string str = null;
    Write(str.Length.ToString());
  }
  catch (Exception e)
  {
    Error(e.Message);
  }
#>
```

## <a name="access-to-host-and-service-provider"></a>Доступ к узлу и поставщику услуг

Свойство `this.Host` может предоставлять доступ к свойствам, предоставляемым узлом, выполняющим шаблон. Для использования необходимо `this.Host` задать `hostspecific` атрибут в `<@template#>` директиве:

`<#@template ... hostspecific="true" #>`

Тип `this.Host` зависит от типа узла, в котором выполняется шаблон. В шаблоне, который выполняется в Visual Studio, можно выполнить приведение к, чтобы `this.Host` `IServiceProvider` получить доступ к службам, таким как интегрированная среда разработки. Пример:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Использование другого набора служебных методов

В рамках процесса формирования текста файл шаблона преобразуется в класс, который всегда называется `GeneratedTextTransformation` и наследуется от <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> . Если вместо этого вы хотите использовать другой набор методов, можно написать собственный класс и указать его в директиве template. Класс должен наследовать от <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

```
<#@ template inherits="MyUtilityClass" #>
```

Используйте `assembly` директиву для ссылки на сборку, в которой можно найти скомпилированный класс.
