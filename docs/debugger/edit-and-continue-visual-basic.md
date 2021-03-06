---
title: Режим "Изменить и продолжить" (Visual Basic) | Документация Майкрософт
description: Для проектов Visual Basic доступен режим "Изменить и продолжить". Из этой статьи вы узнаете, какие правки поддерживаются, а также как управлять их применением.
ms.custom: SEO-VS-2020
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f5df9910d779a4c360a0c1f3b6482b5c51256d29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871927"
---
# <a name="edit-and-continue-visual-basic"></a>Режим "Изменить и продолжить" (Visual Basic)
"Изменить и продолжить" — это режим [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)] для отладки, позволяющий изменять код в режиме приостановки. После применения изменений кода можно возобновить выполнение кода с новыми изменениями и увидеть их эффект.

 Можно использовать режим "Изменить и продолжить" всякий раз в режиме приостановки. В режиме приостановки указатель инструкций (желтая стрелка в окне исходного кода) указывает на строку, содержащую исполняемую инструкцию в теле метода или свойства, которая будет выполнена следующей.

 Операция "Изменить и продолжить" поддерживает большинство изменений, которые могут потребоваться в ходе отладки, но существуют некоторые исключения. Дополнительные сведения см. в разделе [Поддерживаемые изменения кода (C# и Visual Basic)](../debugger/supported-code-changes-csharp.md).

 При несанкционированном изменении, измененный код отмечается фиолетовой волнистой линией и задача отображается в списке задач. Необходимо отменить несанкционированное изменение, если нужно продолжить в режиме "Изменить и продолжить". Некоторые несанкционированные изменения могут быть разрешены, если производить их вне режима "Изменить и продолжить". Если требуется сохранить результат такого несанкционированного изменения, необходимо остановить отладку и перезапустить приложение.

 Режим "Изменить и продолжить" поддерживают приложения UWP для Windows 10, а также 86- и 64-разрядные приложения для классических платформ .NET Framework 4.6 или более поздних версий (платформа .NET Framework поддерживается только для настольных компьютеров).

 > [!NOTE]
 > Не поддерживают платформы ASP.NET 5, Silverlight 5, Windows 8.1 и приложения для них.

 Режим "Изменить и продолжить" не поддерживается при отладке с использованием функции **Присоединение к процессу**. Режим "Изменить и продолжить" не поддерживается при отладке оптимизированного кода, а также смешанного управляемого и машинного кода. Дополнительные сведения см. в разделе [Поддерживаемые изменения кода (C# и Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Подразделы данного раздела предоставляют дополнительные сведения об использовании этого режима и о том, какие виды изменений запрещены.

## <a name="in-this-section"></a>В этом разделе
 [Практическое руководство. Применение изменений в режиме приостановки выполнения с помощью операции "Изменить и продолжить"](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md). Объясняется, как применять изменения кода в режиме приостановки.

 [Поддерживаемые изменения кода (C# и Visual Basic)](../debugger/supported-code-changes-csharp.md). Описываются типы изменений, которые невозможно выполнить в режиме "Изменить и продолжить" [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)].

## <a name="related-sections"></a>Связанные разделы
 [Изменить и продолжить](../debugger/edit-and-continue.md). Предоставляет список разделов по режиму "Изменить и продолжить".
