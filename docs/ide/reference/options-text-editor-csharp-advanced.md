---
title: "\"Параметры\", \"Текстовый редактор\", C#, \"Дополнительно\""
description: Узнайте, как с помощью страницы "Дополнительно" в разделе "C#" изменять параметры для форматирования в редакторе, рефакторинга кода и комментариев XML-документации в C#.
ms.custom: SEO-VS-2020
ms.date: 11/13/2020
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: akhera99
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6e8c235c62eeba394902698ecbfc412ed37b0979
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039896"
---
# <a name="options-text-editor-c-advanced"></a>"Параметры", "Текстовый редактор", C#, "Дополнительно"

Страница **Дополнительно** позволяет изменять параметры для форматирования в редакторе, рефакторинга кода и комментариев XML-документации в C#. Для доступа к этой странице параметров выберите **Сервис** > **Параметры** и затем **Текстовый редактор** > **C#**  > **Дополнительно**.

> [!NOTE]
> Здесь могут быть указаны не все параметры.

## <a name="analysis"></a>Анализ

- Область динамического анализа кода или фонового анализа

   Настройте область фонового анализа для управляемого кода. Дополнительные сведения см. в разделе [Практическое руководство. Настройте область динамического анализа кода для управляемого кода](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

## <a name="using-directives"></a>Директивы using

- Располагать директивы "System" первыми при сортировке using

   При выборе команды **Удалить и сортировать директивы using** в контекстном меню выполняется сортировка директив `using` и помещение пространств имен System в верхнюю часть списка.

   До сортировки:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   После сортировки:

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```

- Разделять группы директив using

   При выборе команды **Удалить и сортировать директивы using** в контекстном меню выполняется отделение `using` путем вставки пустой строки между группами директив, у которых одно и то же корневое пространство имен.

   До сортировки:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   После сортировки:

   ```csharp
   using AutoMapper;

   using FluentValidation;

   using Newtonsoft.Json;

   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```

::: moniker range=">=vs-2019"                                              
- Предлагать using для типов в сборках .NET Framework
::: moniker-end
                                         
::: moniker range="vs-2017"                                                
- Предлагать using для типов в эталонных сборках
::: moniker-end                                                            

- Предлагать using для типов в пакетах NuGet

   При выборе этих параметров доступна команда [Быстрое действие](../quick-actions.md) для установки пакета NuGet и добавления директивы `using` для типов, на которые нет ссылок.

   ![Быстрое действие для установки пакета NuGet в Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Выделение

- Выделить ссылки на символ под курсором

   Когда курсор находится внутри символа либо вы щелкаете его, выделяются все экземпляры этого символа в файле кода.

## <a name="outlining"></a>Структуризация

- Переходить в режим структурирования после открытия файлов

   При выборе автоматически структурирует файл кода, создавая свертываемые блоки кода. При первом открытии файла блоки #regions и неактивные блоки кода свертываются.

- Показывать разделительные линии процедур

   Текстовый редактор показывает визуальную область действия процедур. Линия проводится в исходных файлах *.cs* проекта в расположениях, указанных в следующей таблице:

   |Расположение в исходном файле .cs|Пример расположения линий|
   |---------------------------------|------------------------------|
   |После закрытия конструкции объявления блока|— В конце класса, структуры, модуля, интерфейса или перечисления<br />— После свойства, функции или дочернего элемента<br />— Не между предложениями get и set в свойстве|
   |После набора однострочных конструкций|— После операторов импорта, до определения типа в файле класса<br />— После объявления переменных в классе, до любых процедур|
   |После однострочных объявлений (объявления не на уровне блоков)|— После операторов импорта, операторов наследования, объявлений переменных, объявлений событий, объявлений делегатов и операторов объявления библиотек DLL|

## <a name="block-structure-guides"></a>Направляющие для структуры блоков

Установите этот флажок для отображения пунктирных вертикальных линий между фигурными скобками ( **{}** ) в коде. Это позволит легко определять отдельные блоки кода для уровня объявления и конструкций уровня кода.

## <a name="editor-help"></a>Справка по редактору
::: moniker range=">=vs-2019"
- Подсказки для имен встроенных параметров 
    
    Если этот флажок установлен, то вставляются подсказки имен параметров для литералов, приведенных литералов и создаваемых экземпляров объектов перед каждым аргументом в вызовах функций.  
    
    ![Подсказки для имен встроенных параметров для CSharp](media/inline-parameter-name-hints-csharp.png)

- Подсказки по встроенным типам 
    
    Если этот флажок установлен, то вставляются подсказки по встроенным типам для переменных с выводимыми типами и типами лямбда-параметров.  
    
    ![Подсказки по встроенным типам для CSharp](media/inline-type-hints-csharp.png)
::: moniker-end
- Создавать комментарии XML-документации для ///

   Когда параметр выбран, после ввода начала комментария `///` в XML-документации вставляются XML-элементы для комментариев. Дополнительные сведения о XML-документации см. в разделе [Комментарии к XML-документации (руководство по программированию на C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>См. также

- [Практическое руководство. Вставка XML-комментариев для создания документации](../../ide/reference/generate-xml-documentation-comments.md)
- [Комментарии к XML-документации (руководство по программированию на C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Документирование кода с помощью XML-комментариев (руководство по C#)](/dotnet/csharp/codedoc)
- [Настройка языковых параметров редактора](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
