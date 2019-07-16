---
title: Пошаговое руководство. Отладка во время разработки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54466cc3561c194199bbad2b35cd00433da2b0f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149428"
---
# <a name="walkthrough-debugging-at-design-time"></a>Пошаговое руководство. Отладка во время разработки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно использовать Visual Studio **Интерпретация** окне, чтобы выполнить функцию или подпрограмму, когда приложение не запущено. Если в функции или подпрограмме есть точка останова, Visual Studio прервет выполнение на соответствующей точке. При этом можно использовать окна отладчика для просмотра состояния программы. Эта возможность называется отладкой времени разработки.  
  
 В следующей процедуре показано, как можно использовать эту возможность.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>Чтобы попасть на точки останова из окна "Интерпретация"  
  
1. Вставьте следующий код в консольное приложение Visual Basic:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2. Установите точку останова на строке `s="Add BreakPoint Here"`.  
  
3. Введите следующую команду в **Интерпретация** окна: `?MyFunction<enter>`  
  
4. Убедитесь, что случился останов и что стек вызовов правилен.  
  
5. На **Отладка** меню, щелкните **Продолжить**и убедитесь, что вы по-прежнему в режиме конструктора.  
  
6. Введите следующую команду в **Интерпретация** окна: `?MyFunction<enter>`  
  
7. Введите следующую команду в **Интерпретация** окна: `?MySub<enter>`  
  
8. Убедитесь, что достигнута точка останова и посмотрите значение статической переменной `i` в **"Локальные"** окна. Оно должно иметь значение 3.  
  
9. Убедитесь, что стек вызовов верен.  
  
10. На **Отладка** меню, щелкните **Продолжить**и убедитесь, что вы по-прежнему в режиме конструктора.  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Основы отладки](../debugger/debugger-basics.md)
