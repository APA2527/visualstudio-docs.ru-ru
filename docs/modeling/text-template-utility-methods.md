---
title: Служебные методы для текстовых шаблонов
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c65960b2ad7f0eb31a9c969fb4671f883dc477c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001465"
---
# <a name="text-template-utility-methods"></a>Служебные методы для текстовых шаблонов

Существует несколько методов, которые всегда доступны для вас при написании кода в текстовом шаблоне Visual Studio. Эти методы определяются в <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

> [!TIP]
> Можно также использовать другие методы и служб, предоставляемых средой узла в шаблоне регулярных (без предварительной обработки) текста. К примеру, можно разрешить пути к файлам, журнал ошибок и получение служб, предоставляемых Visual Studio и любой загруженных пакетов. Дополнительные сведения см. в разделе [доступ к Visual Studio из текстового шаблона](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

## <a name="write-methods"></a>Написание методов

Можно использовать `Write()` и `WriteLine()` методы можно добавлять текст в стандартный блок кода, вместо использования блока кода выражения. В следующих блоках кода функционально эквивалентны.

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

### <a name="code-block-using-writeline"></a>Блок кода, с помощью WriteLine()

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

Может оказаться полезным использовать один из этих служебных методов вместо блока выражения в длинном блоке кода с вложенные структуры управления.

`Write()` И `WriteLine()` методы имеют две перегруженные версии, одна из которых принимает один строковый параметр и один принимает строку составного формата, а также массив объектов для включения в строку (например `Console.WriteLine()` метод). Следующие два применения `WriteLine()` функционально эквивалентны:

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

## <a name="indentation-methods"></a>Методы для отступов

Можно использовать методы отступа для форматирования вывода текстового шаблона. <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> Класс имеет `CurrentIndent` строковое свойство, которое отображает текущий отступ в текстовом шаблоне и `indentLengths` поле, то есть список отступы, которые были добавлены. Вы можете добавить отступ с `PushIndent()` метод и удалить отступ с `PopIndent()` метод. Если вы хотите удалить все отступы, используйте `ClearIndent()` метод. Следующий блок кода показано использование этих методов:

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

Этот блок кода выводит следующие результаты:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Методы ошибок и предупреждений

Ошибки и предупреждения служебные методы можно использовать для добавления сообщений в списке ошибок Visual Studio. Например следующий код будет добавить сообщение об ошибке в списке ошибок.

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

## <a name="access-to-host-and-service-provider"></a>Доступ к узлу и поставщика услуг

Свойство `this.Host` можно предоставить доступ к свойствам, предоставляемым основным приложением, выполняющего шаблона. Чтобы использовать `this.Host`, необходимо задать `hostspecific` атрибут в `<@template#>` директивы:

`<#@template ... hostspecific="true" #>`

Тип `this.Host` зависит от типа узла, в котором выполняется шаблон. В шаблоне, на котором выполняется в Visual Studio, можно привести `this.Host` для `IServiceProvider` для получения доступа к службам, например интегрированной среды разработки. Пример:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>С помощью другой набор служебных методов

Как часть в процессе создания текста, файл шаблона преобразуется в класс, который всегда имеет имя `GeneratedTextTransformation`и наследует от <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Если вы хотите использовать другой набор методов, можно написать собственный класс и укажите его в директиве template. Этот класс должен наследовать из <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

```
<#@ template inherits="MyUtilityClass" #>
```

Используйте `assembly` директива для ссылки на сборку, где находится скомпилированный класс.