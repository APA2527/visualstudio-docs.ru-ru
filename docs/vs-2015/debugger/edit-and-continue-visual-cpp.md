---
title: Edit and Continue (Visual C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fef02f08ac635687eaaf071188ba0455c6389d9e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301062"
---
# <a name="edit-and-continue-visual-c"></a>Edit and Continue (Visual C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете использовать функцию "Изменить и продолжить" в проектах Visual C++. See [Supported Code Changes (C++)](../debugger/supported-code-changes-cpp.md) for information about the limitations of Edit and Continue.  
  
 Starting in Visual Studio 2015 Update 1, you can now use Edit and Continue in Windows Store C++ apps and DirectX apps, because it now supports the **/ZI** compiler switch with **/bigobj** switch. You can also use Edit  and Continue with binaries compiled with the **/FASTLINK** switch.  
  
 Other Update 1 improvements include a new, cancelable wait dialog, and notification when a file does not support Edit and Continue. For more information about Update 1 improvements, see [Improvements for C++ Edit and Continue in Visual Studio 2015 Update 1](https://devblogs.microsoft.com/cppblog/improvements-for-c-edit-and-continue-in-visual-studio-2015-update-1/).  
  
 Параметр компилятора [/Zo (Enhance Optimized Debugging)](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f), который появился в Visual Studio 2013 с обновлением 3, добавляет дополнительные сведения в PDB-файлы символов для двоичных файлов, скомпилированных без параметра [/Od (Disable (Debug))](https://msdn.microsoft.com/library/aafb762y.aspx).  
  
 **/Zo** disables Edit and Continue. См. раздел [Практическое руководство. Отладка оптимизированного кода](../debugger/how-to-debug-optimized-code.md)  
  
## <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Включение и отключение возможности "Изменить и продолжить".  
 Можно отключить автоматический вызов возможности "Изменить и продолжить" при внесении изменений в код, которые не следует применять в текущем сеансе отладки. Можно также повторно включить автоматическую возможность "Изменить и продолжить".  
  
1. В меню **Сервис** выберите пункт **Параметры**.  
  
2. В окне **Параметры** выберите папку **Отладка -&gt; Общие**.  
  
3. В группе **Изменить и продолжить** установите или снимите флажок **Включить собственную операцию "Изменить и продолжить"** .  
  
   Изменение этого параметра влияет на все проекты, над которыми вы работаете. После изменения этого параметра не требуется производить повторную сборку приложения. Этот параметр можно изменять даже во время отладки. Если сборка приложения осуществляется из командной строки или из Makefile, а его отладка происходит в окружении Visual Studio, возможность "Изменить и продолжить" можно по-прежнему использовать, если задать параметр **/ZI** .  
  
## <a name="BKMK_How_to_apply_code_changes_explicitly"></a> Применение изменений кода явным образом  
 В Visual C++ возможность "Изменить и продолжить" может применять изменения кода двумя способами. Изменения кода могут быть применены неявно (при выборе команды выполнения) или явно (при использовании команды **Применить изменения кода** ).  
  
 При явном применении изменений кода программа остается в режиме приостановки — выполнение не продолжается.  
  
- Для применения изменений кода явным образом в меню **Отладка** выберите **Применить изменения кода**.  
  
## <a name="BKMK_How_to_stop_code_changes"></a> Остановка внесения изменений в код  
 Пока режим "Изменить и продолжить" находится в процессе внесения изменений в код, можно остановить эту операцию.  
  
 Для остановки внесения изменений в код:  
  
- В меню **Отладка** выберите команду **Остановить применение изменений кода**.  
  
  Этот пункт меню становится видимым только в процессе внесения изменений в код.  
  
  При выборе этого параметра никакие изменения в коде не фиксируются.  
  
## <a name="BKMK_How_to_reset_the_point_of_execution"></a> Сброс точки выполнения  
 Некоторые изменения в коде могут вызвать перемещение точки выполнения в новое расположение, после того как эти изменения будут применены операцией "Изменить и продолжить". Операция "Изменить и продолжить" стремится разместить точку выполнения с максимально возможной точностью, однако в некоторых случаях результаты могут быть неверными.  
  
 В Visual C++ о перемещении точки выполнения сообщает диалоговое окно. Прежде чем продолжить процесс отладки, необходимо проверить, что точка установлена правильно. Если это не так, необходимо использовать команду **Задать следующий оператор** . Дополнительные сведения см. в разделе [Задание следующего оператора для выполнения](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
## <a name="BKMK_How_to_work_with_stale_code"></a> Работа с устаревшим кодом  
 В некоторых случаях операция "Изменить и продолжить" не может немедленно внести изменения в исполняемый код, но может внести их позже, если отладка будет продолжена. Это происходит при изменении функции, вызвавшей текущую выполняемую функцию, или при добавлении новых переменных объемом более 64 байт в функцию, которая находится в стеке вызовов.  
  
 В таких случаях отладчик продолжает выполнение исходного кода до тех пор, пока эти изменения не вступят в силу. Устаревший код отображается в качестве временного исходного файла в отдельном окне исходного кода. Заголовок этого окна имеет вид наподобие `enc25.tmp`. При этом отредактированный исходный код остается в своем окне. При попытке редактирования устаревшего кода появляется предупреждение.  
  
## <a name="see-also"></a>См. также раздел  
 [Поддерживаемые изменения кода (C++)](../debugger/supported-code-changes-cpp.md)
