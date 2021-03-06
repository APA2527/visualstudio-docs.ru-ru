---
title: Переход к файлу, переход к символу, переход к строке
description: Сведения о командах перехода в Visual Studio и о том, как использовать их для выполнения направленного поиска в вашем коде.
ms.custom: SEO-VS-2020
ms.date: 08/14/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3e000224fc09810e15ba3cdbdc4be729139eaaa
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597539"
---
# <a name="find-code-using-go-to-commands"></a>Поиск в коде с использованием команд перехода

Команда **Перейти** в Visual Studio используется для направленного поиска кода и помогает быстро находить указанные элементы. Используя простой унифицированный интерфейс, вы можете перейти к конкретной строке, типу, символу, файлу и члену.

## <a name="how-to-use-it"></a>Способ использования

Входные данные | Функция
------------ | ---
**Клавиатура** | Нажмите клавиши **CTRL**+**T** или **CTRL**+ **,**
**Мышь** | Выберите **Правка** > **Перейти к** > **Перейти ко всем**

В верхней правой части редактора кода отображается небольшое окно.

![Окно "Перейти ко всем"](media/go-to-all.png)

По мере ввода результаты будут отображаться в раскрывающемся списке под текстовым полем. Чтобы перейти к элементу, выберите его в списке.

![Окно "Перейти"](../ide/media/vside_navigatetowindow.png)

Вы также можете ввести вопросительный знак ( **?** ), чтобы получить дополнительную справку.

![Справка по команде "Перейти ко всем"](media/go-to-all-help.png)

## <a name="filtered-searches"></a>Отфильтрованные поиски

По умолчанию поиск заданного элемента осуществляется во всех элементах решения. Тем не менее можно ограничить область поиска в коде конкретными типами элементов, указав перед условием поиска соответствующие символы. Также можно быстро изменить фильтр поиска с помощью кнопок на панели инструментов диалогового окна **Перейти**. Кнопки слева позволяют сменить фильтры типов, а справа — область поиска.

![Переход к членам](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>Фильтрация определенного типа элемента кода

Чтобы сузить область поиска до определенного типа элемента кода, можно указать префикс в поле поиска или выбрать один из пяти значков фильтра:

Prefix | Значок | Сочетание клавиш | Описание
:-: | - | - | -
:| ![Значок строки](media/gotoall-line-icon.png) | **CTRL**+**G** | Переход к строке с указанным номером
f| ![Значок файлов](media/gotoall-files-icon.png) | **CTRL**+**1**, **CTRL**+**F** | Переход к указанному файлу
r| ![Значок последних файлов](media/gotoall-recent-files-icon.png) | **CTRL**+**1**, **CTRL**+**R** | Переход к указанному, недавно просмотренному файлу
t| ![Значок типов](media/gotoall-types-icon.png) | **CTRL**+**1**, **CTRL**+**T** | Переход к указанному типу
m| ![Значок членов](media/gotoall-members-icon.png) | **CTRL**+**1**, **CTRL**+**M** | Переход к указанному члену
\#| ![Значок символов](media/gotoall-symbols-icon.png) | **CTRL**+**1**, **CTRL**+**S** | Переход к указанному символу

### <a name="filter-to-a-specific-location"></a>Фильтрация определенного расположения

Чтобы сузить область поиска до определенного расположения, выберите один из двух значков документов:

Значок | Описание
---- | ---
![Текущий документ](media/gotoall_currentdocument.png) | Поиск только в текущем документе
![Внешние документы](media/gotoall_external.png) | Поиск во внешних документах наряду с документами, находящимися в проекте или решении

## <a name="camel-casing"></a>"Верблюжий" стиль

Если в коде используется ["верблюжий" стиль](https://en.wikipedia.org/wiki/Camel_case), можно ускорить поиск элементов кода за счет ввода только прописных букв в имени элемента кода. Например, если код содержит тип `CredentialViewModel`, можно сузить поиск, выбрав фильтр по **типу** (**t**) и введя только прописные буквы в имени (`CVM`) в диалоговом окне "Перейти". Эта функция полезна, если код содержит длинные имена.

![Окно "Перейти" — поиск по прописным буквам](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>Параметры

Выберите значок шестеренки ![Значок шестеренки](media/gotoall_gear.png) , чтобы изменить режим работы этой функции:

Параметр | Описание
------- | ---
Использовать вкладку предварительного просмотра | Немедленное отображение выбранного элемента на вкладке предварительного просмотра в интегрированной среде разработки
Отображение сведений | Отображение в окне сведений о проекте, файле, строке и сводных данных из комментариев к документации
Центрировать окно | Перемещение этого окна в верхнюю среднюю часть редактора кода, а не в правый верхний угол

## <a name="see-also"></a>См. также

- [Навигация по коду](../ide/navigating-code.md)
- [Диалоговое окно "Перейти к строке"](../ide/reference/go-to-line.md)
- [Функции "Перейти к определению" и "Показать определение"](../ide/go-to-and-peek-definition.md)
