---
title: Как задать точки останова в рабочих процессах (прежние версии) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 182f28a2b21ae3129ce0d34fae97280ba0a07218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603595"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Как задать точки останова в рабочих процессах (для прежних версий)
В этом разделе описывается задание точек останова в приложениях [!INCLUDE[wf](../includes/wf-md.md)], построенных с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий. Используйте средство [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий, если приложение [!INCLUDE[wf2](../includes/wf2-md.md)] должно ориентироваться на [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 При использовании средства [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий в среде [!INCLUDE[vs2010](../includes/vs2010-md.md)] для построения приложения [!INCLUDE[wf2](../includes/wf2-md.md)] точки останова в коде на языке C# или Visual Basic можно задавать так же, как в Visual Studio. Как ожидалось, выполнение рабочего процесса останавливается в каждой заданной точке останова.

 Точка останова имеет три состояния: *Pending*, *Bounds*и *Error*. При установке точки останова она имеет состояние Ожидание, которое представлено пустым красным значком. Когда среда выполнения загружает тип рабочего процесса, выполняется переход в состояние Привязка, которое представлено сплошным красным значком. Если задать неправильный формат для точки останова, как для неправильного имени действия, появляется окно сообщений об ошибке. Точка останова останется в окне точек останова, но будет отмечена маленьким «х».

 Можно установить точки останова в действии в рабочей области конструктора рабочих процессов следующими способами:

- Щелкните действие правой кнопкой мыши и выберите пункт **точка останова \ вставить точку останова**.

- Выделите действие и нажмите клавишу F9.

- Выберите **создать точку останова** в меню **Отладка** .

     Этот вариант также можно использовать для установки новой точки останова при отладке, когда отладчик останавливается в точке останова.

    > [!NOTE]
    > Задание точек останова в вызванных рабочих процессах не поддерживается.

### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Чтобы задать точку останова с использованием команды "Создать точку останова" из меню "Отладка"

1. В меню **Отладка** выберите пункт **создать точку останова**.

2. Нажмите кнопку **прервать в функции**.

     Откроется диалоговое окно **Новая точка останова** .

3. Укажите имя действия в текстовом поле **функции** , используя следующий синтаксис: `QualifiedActivityId[:[FullClassName][:InstanceId]]` .

    > [!NOTE]
    > При необходимости вместо использования имени действия в текстовом поле **функция** можно установить точку останова, указав абсолютный путь к действию рабочего процесса. Например, предположим, что имеется решение рабочего процесса с именем **WorkflowConsoleApplication1** и рабочий процесс в решении с именем **Workflow1** , которое использует действие с именем **Delay1**. Можно использовать имя действия **Delay1** или указать путь как **Delay1: WorkflowConsoleApplication1. Workflow1** или **Delay1: WorkflowConsoleApplication1. Workflow1: {6614886A-608E-412B-BF98-99FF1559DDDF}**.

4. Установите флажок **использовать IntelliSense** для проверки имени функции.

     Если этот флажок не установлен, то проверка имени точки останова не выполняется.

5. Выберите **Рабочий процесс** из списка **язык** .

6. Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также:
 [Отладка устаревших рабочих процессов](../workflow-designer/debugging-legacy-workflows.md) [вызов отладчика Visual Studio для Windows Workflow Foundation (прежние версии)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)