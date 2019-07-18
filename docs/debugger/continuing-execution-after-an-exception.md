---
title: Продолжение выполнения после исключения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: d557fc0ec056cac22603338f95920e5c721f67dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564103"
---
# <a name="continuing-execution-after-an-exception"></a>Возобновление выполнения после исключения
Когда отладчик приостанавливает выполнение из-за исключения, вы увидите **помощника по исправлению ошибок**, по умолчанию. Если вы отключили **помощника по исправлению ошибок** в **параметры** диалоговом окне вы увидите **исключениям** (C# или Visual Basic) или  **Исключение** диалоговое окно (C++).

 Когда **помощника по исправлению ошибок** отображается, можно попытаться устранить неполадку, вызвавшую исключение.

## <a name="managed-and-native-code"></a>Управляемого и машинного кода
 В управляемого и машинного кода можно возобновить выполнение в том же потоке после необработанного исключения. **Помощника по исправлению ошибок** стек вызовов в точке, где возникло исключение.

## <a name="mixed-code"></a>Смешанный код
 Если при отладке смешанного машинного и управляемого кода возникает необрабатываемое исключение, ограничения операционной системы не позволяют очистить стек вызовов. При попытке очистить стек вызовов с помощью контекстного меню отображается сообщение об ошибке, поясняющее, что при отладке смешанного кода отладчик не может вернуться в предыдущее состояние после возникновения необрабатываемого исключения.

## <a name="see-also"></a>См. также

- [Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md)