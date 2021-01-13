---
title: Поиск выполняющегося процесса ASP.NET | Документация Майкрософт
description: Узнайте, как выполнить отладку выполняющегося приложения ASP.NET. Подключите отладчик Visual Studio к процессу ASP.NET по имени.
ms.custom: SEO-VS-2020
ms.date: 11/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 07d692dac1b5770cdee4682af5184649471c2828
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903445"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Поиск имени процесса ASP.NET

Чтобы выполнить отладку выполняющегося приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], отладчик Visual Studio должен присоединиться к процессу [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] по имени.

**Чтобы узнать, какой процесс выполняет приложение ASP.NET:**

1. После запуска приложения в Visual Studio выберите пункт **Отладка** > **Присоединить к процессу**.

1. В диалоговом окне **Присоединиться к процессу** введите первые буквы имен процессов из следующего списка или введите их в поле поиска. Работающий процесс — это процесс, выполняющий приложение ASP.NET. Подключитесь к этому процессу, чтобы выполнить отладку приложения.

    - *w3wp.exe* — это IIS версии 6.0 и более поздних версий.
    - *aspnet_wp.exe* — более ранние версии IIS.
    - *iisexpress. exe* — это IISExpress.
    - *dotnet.exe* — это ASP.NET Core.
    - *inetinfo.exe* — это старые приложения ASP, выполняющиеся в процессе.

>[!NOTE]
>Код [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] для Visual Studio 2012 и более ранние версии может находиться в файловой системе и запускаться на тестовом сервере *WebDev.WebServer.exe* или *WebDev.WebServer40.exe*. В этом случае для локальной отладки подключитесь к *WebDev.WebServer.exe* или *WebDev.WebServer40.exe*, а не к процессу [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

**См. также:**

- [Присоединение к выполняемому процессу](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Предварительные требования для удаленной отладки веб-приложений](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Требования к системе](../debugger/aspnet-debugging-system-requirements.md)
- [Отладка приложений ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)