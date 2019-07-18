---
title: Just-In-Time, отладка, диалоговое окно параметров | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23a285cf0ce017130a5fe76171c50082362e4856
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905939"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Страница "JIT-отладка", папка "Отладка", диалоговое окно "Параметры"
Чтобы получить доступ к странице **JIT**, перейдите к меню **Сервис** и щелкните пункт **Параметры**. В диалоговом окне **Параметры** разверните узел **Отладка** и выберите **JIT**. Эта страница позволяет включить JIT-отладку для управляемого кода, машинного кода и скриптов. Дополнительные сведения см. в разделе [JIT-отладка](../debugger/just-in-time-debugging-in-visual-studio.md).

 JIT-отладку можно разрешить для программ следующих типов:

- Управляемый

- машинный код;

- Сценарий

  JIT-отладка — это технология отладки программы, запускаемой вне [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Программу, созданную в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], можно выполнять вне среды [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Если включена JIT-отладка, сбой программы вызовет появление диалогового окна с вопросом о том, необходимо ли выполнить отладку.

## <a name="associated-warnings"></a>Связанные предупреждения
 При посещении этой страницы из диалогового окна **Параметры** можно увидеть предупреждающее сообщение, например следующего содержания:

 **В качестве JIT-отладчика был зарегистрирован другой отладчик. Для восстановления включите JIT-отладку или запустите средство восстановления Visual Studio.**

 Это сообщение возникает, если в качестве JIT-отладчика установлен другой отладчик, возможно, отладчик [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] более старой версии.

 Также возможно отображение следующего сообщения:

 **Обнаружены ошибки регистрации JIT-отладки. Для восстановления включите JIT-отладку или запустите средство восстановления Visual Studio.**

 Если отобразилось любое из этих предупреждений, для JIT-отладки с [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] необходимы права администратора до тех пор, пока проблема не будет устранена. Если попытаться разрешить проблему, не имея прав администратора, возникает следующее сообщение об ошибке:

 **Отказано в доступе. Администратор должен включить JIT-отладку или восстановить установку Visual Studio.**

## <a name="see-also"></a>См. также
- [Папка "Отладка", диалоговое окно "Параметры"](../debugger/debugging-options-dialog-box.md)
- [Практическое руководство. Установка параметров отладчика](../debugger/how-to-specify-debugger-settings.md)