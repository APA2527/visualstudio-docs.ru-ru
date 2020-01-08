---
title: "\"Параметры\", \"Текстовый редактор\", C/C++, \"Форматирование\""
ms.date: 04/30/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- CPP
helpviewer_keywords:
- Text Editor Options dialog box, formatting
- ClangFormat
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: d7a6029058ab0bc02a623df0e1733eb8548102d5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596259"
---
# <a name="options-text-editor-cc-formatting"></a>"Параметры", "Текстовый редактор", C/C++, "Форматирование"

Используйте страницы свойств, чтобы изменять поведение по умолчанию редактора кода при написании программ на языках C и C++.

![Страницы свойств форматирования C++](media/cpp-formatting.png)

Чтобы открыть эту страницу, в диалоговом окне **Параметры** в левой области разверните **Текстовый редактор**, **C/C++** и щелкните **Форматирование**.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Страница «Общие»

Эта страница содержит параметры для форматирования операторов и блоков при их вводе.

::: moniker range="vs-2017"

**Visual Studio 2017 версии 15.7 и выше**:

::: moniker-end

страница также содержит параметры для настройки поддержки [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) версии 5.0. ClangFormat — это служебная программа, которая упрощает задание стиля и формата кода на основе набора правил, которые можно настроить в файле .clang-format или _clang-format.

### <a name="configuring-clangformat-options"></a>Настройка параметров ClangFormat

::: moniker range="vs-2017"

**Visual Studio 2017 версии 15.7 и выше**:

::: moniker-end

Поддержка ClangFormat включена по умолчанию. Вы можете выбрать, какие из этих общих соглашений о форматировании должны применяться ко всем вашим проектам: LLVM, Google, Chromium, Mozilla или WebKit. Можно также создать файл .clang-format или _clang-format для настраиваемого определения формата. Такой файл уже присутствует в папке проекта, Visual Studio использует его для форматирования всех файлов исходного кода в этой папке и вложенных в нее папках.

По умолчанию Visual Studio выполняет clangformat.exe в фоновом режиме, применяя форматирование по мере ввода. Можно также указать, чтобы эта программа запускалась только для вызываемых вручную команд форматирования **Форматировать документ (CTRL+K, CTRL+D)** или **Форматировать выбранный фрагмент (CTRL+K, CTRL+F)** .

## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Страницы "Отступ", "Новые строки", "Spacing Wrapping" (Перенос пробелов)

Эти страницы позволяют использовать различные настройки форматирования, но игнорируются, если включен ClangFormat.

## <a name="see-also"></a>См. также

- [Страница "Общие", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/general-environment-options-dialog-box.md)
- [Использование технологии IntelliSense](../../ide/using-intellisense.md)
