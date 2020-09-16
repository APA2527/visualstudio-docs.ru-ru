---
title: Отладка функций Windows API | Документация Майкрософт
ms.custom: seodec18
ms.date: 06/03/2020
ms.topic: how-to
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f7b293270facbbfa0d2174121ff6a3ac736b75a
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599883"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Как отладить функции Windows API?
Если нужно отладить функцию Windows API с загруженными символами NT, необходимо выполнить следующие действия.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Установка точки останова в функции Windows API с загруженными символами NT

- В диалоговом окне [Точка останова в функции](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file) введите имя функции вместе с именем DLL-файла, в котором эта функция находится (см. статью [Оператор контекста в отладчике Visual Studio (C++)](../debugger/context-operator-cpp.md)). В 32-разрядном коде используйте декорированную форму имени функции. Например, чтобы задать точку останова на **MessageBeep**, необходимо ввести следующее.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Чтобы получить внутреннее имя, обратитесь к разделу [Просмотр внутренних имен](/previous-versions/5x49w699(v=vs.140)).

     Можно проверить внутреннее имя и просмотреть его в дизассемблированном коде. При паузе в выполнении функции в отладчике Visual Studio щелкните функцию правой кнопкой мыши в окне редактора кода или окне стека вызовов выберите **К дизассемблированному коду**.

- В 64-разрядном коде можно использовать недекорированное имя.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>См. также
- [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)