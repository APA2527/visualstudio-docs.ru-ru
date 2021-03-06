---
title: Изменение клавиши справки F1
description: Сведения о том, как изменить или удалить сопоставление для клавиши F1
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
robots: noindex,nofollow
manager: jillfra
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: d9add6996949a97d6140ab6d063f13e02b677e79
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684081"
---
# <a name="change-the-f1-help-key-in-visual-studio"></a>Изменение клавиши справки F1 в Visual Studio

Если вам нужно назначить для клавиши F1 другую функцию, кроме запуска службы "Справка F1", или полностью отключить вызов справки с помощью клавиши F1, вы можете удалить или изменить сопоставление клавиши.

> [!IMPORTANT]
> Если вы хотите отключить справку F1 из-за проблем с производительностью, мы рекомендуем временно изменить сопоставление клавиши, чтобы вы и дальше могли тестировать улучшения службы "Справка F1" в последующих обновлениях Visual Studio. В большинстве случаев F1 применяется для быстрого вызова справочника по ключевым словам языка и API-интерфейсам из редактора кода страниц или для доступа к справке по окнам или элементам пользовательского интерфейса в интегрированной среде разработки. Если вы отключите эту клавишу, она перестанет выполнять любые функции в Visual Studio.

**Чтобы отключить справку F1, выполните следующие действия:**

1. В Visual Studio выберите **Средства** > **Параметры**, а затем — **Среда** и **Клавиатура**.

1. В текстовом поле **Показать команды, содержащие** введите **Help.f1**, чтобы применить фильтр к списку команд.

   ![Отключение справки F1](../not-in-toc/media/disable-f1-help-key.png)

1. Щелкните **Удалить**, чтобы удалить сопоставление клавиши.

1. Выберите текстовое поле **Клавиши**.

1. Нажмите на клавиатуре новую клавишу или используйте сочетание клавиш для вызова справки F1, например **ALT+F1**, затем щелкните **Назначить** и нажмите кнопку **ОК**.

См. дополнительные сведения об [определении и настройке сочетаний клавиш](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
