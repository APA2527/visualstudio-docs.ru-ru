---
title: Возобновление выполнения после исключения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e94867d845988b787247c32d32afd35af946972
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350684"
---
# <a name="continuing-execution-after-an-exception"></a>Возобновление выполнения после исключения
Когда отладчик приостанавливает выполнение из-за возникновения исключения, по умолчанию открывается диалоговое окно **Помощник по исправлению ошибок**. Если **Помощник по исправлению ошибок** отключен в диалоговом окне **Параметры**, в этом случае появляется диалоговое окно **Помощник по исключениям** (в C# или Visual Basic) или **Исключение** (в C++).

 Когда появляется диалоговое окно **Помощник по исключениям**, можно попытаться устранить проблему, вызвавшую исключение.

## <a name="managed-and-native-code"></a>Управляемый и машинный код
 В случае управляемого и машинного кода можно возобновить выполнение в том же потоке после необработанного исключения. **Помощник по исключениям** очищает стек вызовов до точки, в которой возникло исключение.

## <a name="mixed-code"></a>Смешанный код
 Если при отладке смешанного машинного и управляемого кода возникает необрабатываемое исключение, ограничения операционной системы не позволяют очистить стек вызовов. При попытке очистить стек вызовов с помощью контекстного меню отображается сообщение об ошибке, поясняющее, что при отладке смешанного кода отладчик не может вернуться в предыдущее состояние после возникновения необрабатываемого исключения.

## <a name="see-also"></a>См. также

- [Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md)