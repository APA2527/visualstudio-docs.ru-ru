---
title: Практическое руководство. создать XML-фрагменты
description: Узнайте, как использовать редактор XML в Visual Studio для создания XML-фрагментов, позволяющих быстрее создавать XML-файлы.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d935f479e3133db8fb5340359d6a354058a3020a
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400034"
---
# <a name="how-to-create-xml-snippets"></a>Практическое руководство. Создание фрагментов XML

Редактор XML можно использовать для создания новых фрагментов XML. Редактор включает XML-фрагмент с именем «Фрагмент», являющийся заготовкой для создания новых XML-фрагментов.

## <a name="to-create-a-new-xml-snippet"></a>Создание нового XML-фрагмента

Чтобы создать новый фрагмент XML, создайте новый файл XML и щелкните **Вставить фрагмент**.

1. В меню **Файл** щелкните **Создать** и **Файл**.

2. Выберите **Файл XML** и щелкните **Открыть**.

3. Щелкните правой кнопкой мыши панель редактора и выберите **Вставить фрагмент**.

4. Выберите в списке **Фрагмент** и нажмите клавишу **ВВОД**.

5. Внесите произвольные изменения в новый фрагмент.

6. В меню **Файл** выберите **Сохранить XMLFile.xml**.

     Отобразится диалоговое окно **Сохранение файла**.

7. Введите имя нового фрагмента и выберите **Файлы фрагментов** в раскрывающемся окне **Тип файла**.

8. С помощью раскрывающегося списка **Сохранить в** измените расположение для хранения файла на папку *My Documents\Visual Studio 2005\Code Snippets\XML\My XML Snippets* и щелкните **Сохранить**.

## <a name="snippet-description"></a>Описание фрагмента

В этом разделе описываются некоторые ключевые элементы в заготовке фрагмента. См. сведения об [элементах схемы, используемых в фрагментах XML](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>SnippetType, элемент

Редактор поддерживает два типа фрагментов:

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

Тип `Expansion` определяет, должен ли появляться фрагмент при вызове команды **Вставить фрагмент**. Тип `SurroundsWith` определяет, должен ли появляться фрагмент при вызове команды **Разместить во фрагменте**.

### <a name="code-element"></a>Code, элемент

Элемент `Code` определяет XML-текст, который будет вставляться при вызове фрагмента.

> [!NOTE]
> Текст XML-фрагмента необходимо включить в раздел `<![CDATA[...]]>`.

Далее приведен элемент `Code`, созданный с помощью заготовки фрагмента.

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

Элемент `Code` включает три переменные.

- Переменная $name$ определяется пользователем. Она создает элемент `name`, содержащий редактируемое значение, по умолчанию равное «name». Пользовательские переменные определяются с помощью элемента `Literal`.

- Переменная $selected$ является стандартной. Она представляет текст, выделенный в редакторе XML до вызова фрагмента. Размещение этой переменной определяет, где во фрагменте кода, окружающем выделенный текст, будет помещен сам выделенный текст.

- Переменная $end$ является стандартной. Когда пользователь нажимает клавишу **ВВОД**, чтобы завершить редактирование полей фрагмента, эта переменная определяет, куда перемещается знак вставки (^).

  Приведенный выше элемент `Code` вставляет следующий текст XML:

```xml
<test>
  <name>name</name>
</test>
```

Значение элемента имени помечено как редактируемая область.

### <a name="literal-element"></a>Literal, элемент

Элемент `Literal` используется для определения текста замены, который можно изменить после вставки его в файл. Например, в качестве литералов могут быть объявлены строковые литералы, числовые значения и некоторые имена переменных. Можно определить любое количество литералов в XML-фрагменте, и к ним можно обращаться из фрагмента несколько раз. Далее приведен пример элемента `Literal`, определяющего переменную $name$, значение которой по умолчанию равно «name».

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

Литералы также могут ссылаться на функции. Редактор XML включает функцию **LookupPrefix**. Функция **LookupPrefix** выполняет поиск заданного URI пространства имен, начиная с того места в документе XML, из которого был вызван фрагмент, возвращает префикс пространства имен, определенный для этого пространства имен (если он есть), и включает в это имя двоеточие (:). Далее приведен пример элемента `Literal`, в котором используется функция **LookupPrefix**.

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

Переменная $prefix$ может использоваться в любой части XML-фрагмента.

## <a name="see-also"></a>См. также

- [Фрагменты XML](../xml-tools/xml-snippets.md)
- [Практическое руководство. Использование фрагментов XML](../xml-tools/how-to-use-xml-snippets.md)
- [Практическое руководство. Создание фрагмента XML из схемы XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
