---
title: Изменить и продолжить (Visual C#) | Документация Майкрософт
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Edit and Continue
- Edit and Continue [C#]
- debugging [C#], Edit and Continue
ms.assetid: 591bd1b7-ef10-4d10-817b-3f92ca4be006
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 972ad0d772eee9b876f43bc3e2fcd032d4b7e0ab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851015"
---
# <a name="edit-and-continue-visual-c"></a>Режим "Изменить и продолжить" (Visual C#)
 С помощью операции "Изменить и продолжить" для С# в процессе отладки можно вносить изменения в код в режиме приостановки выполнения. Изменения могут применяться без необходимости остановки и повторного запуска сеанса отладки. В режиме выполнения редактор исходного кода доступен только для чтения.

 Операция "Изменить и продолжить" поддерживает большинство изменений, которые могут потребоваться в ходе отладки, но существуют некоторые исключения. Дополнительные сведения см. в разделе [поддерживаемые изменения кода (C# и Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Изменить и продолжить поддерживается в универсальной платформы Windows в Windows 10 и x86 и x64 приложениях, предназначенных для .NET Framework 4.6 рабочего стола или более поздней версии, (.NET Framework является только версии настольного компьютера).

 > [!NOTE]
 > Неподдерживаемые приложения и платформы включают ASP.NET 5, Silverlight 5 и Windows 8.1.

 Когда операция "Изменить и продолжить" включена, поддерживаемые изменения применяются автоматически при использовании команд отладчика, таких как **Продолжить**, **Шаг**, **Задать следующий оператор**, или при выполнении вычисления функции в окне отладчика.

 Дополнительные сведения см. в разделе [Как использовать режим "Изменить и продолжить" (C#)](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>См. также
- [Практическое руководство. Использование режима "Изменить и продолжить" (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [Поддерживаемые изменения кода (C# и Visual Basic)](../debugger/supported-code-changes-csharp.md)