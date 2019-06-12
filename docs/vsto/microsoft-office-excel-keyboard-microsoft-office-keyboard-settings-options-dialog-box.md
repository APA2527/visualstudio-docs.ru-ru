---
title: Клавиатуры Excel Office, настройки клавиатуры, диалоговое окно "Параметры"
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 090e943df2b61352c2342218c3c71c8f0e60eaad
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836035"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Excel Keyboard, настройки клавиатуры Microsoft Office, диалоговое окно "Параметры"
  Microsoft Office Excel и Visual Studio, как обрабатывать сочетания клавиш. Же сочетания клавиш могут соответствовать разным командам в Excel и в Visual Studio. Когда Excel открыт в проекте уровня документа в Visual Studio, только одно приложение за раз получает сочетания клавиш. По умолчанию Visual Studio получает нажатие сочетания клавиш, но может сделать их получения, если документ имеет фокус, выбрав Excel **Инамическая схема клавиатуры**.

 При использовании клавиш, которое не назначено команде, в приложении, которое в настоящий момент обрабатывает сочетания клавиш клавиша передается другие приложения.

 Параметр будет работать для проектов Excel, пока вы не измените его. Выбор не влияет на проекты Microsoft Office Word; необходимо выполнять изменений для Word с использованием Microsoft Office Word сочетания параметров.

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса
 **Схема клавиатуры Visual Studio** Visual Studio получает нажатие сочетания клавиш, даже если фокус находится в Excel. Например, если вы нажмите функциональную клавишу **F5** Excel имеет фокус, Visual Studio запускает отладку решения.

 **Динамическая схема клавиатуры** Visual Studio получает сочетания клавиш только в том случае, когда на него установлен фокус. Если приложение Excel имеет фокус, Excel получает нажатие сочетания клавиш. Например, если вы нажмите функциональную клавишу **F5** Excel имеет фокус, приложение Excel открылось **перейти к** диалоговое окно. Если нажать клавишу **F5** Visual Studio имеет фокус, Visual Studio запускает отладку решения.

## <a name="see-also"></a>См. также
- [Microsoft Office Word Keyboard, настройки клавиатуры Microsoft Office, диалоговое окно "Параметры"](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
