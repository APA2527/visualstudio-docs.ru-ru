---
title: Практическое руководство. Отладка веб-приложений | Документация Майкрософт
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
- Web services, debugging
- ASP.NET Web Forms, debugging
- ASP.NET, debugging Web applications
- debugging ASP.NET Web applications, during development
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd3cbbcd740c0f124b8ab4379204a9d425cd541c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205405"
---
# <a name="how-to-debug-web-applications"></a>Практическое руководство. Отладка веб-приложений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] – Это основная технология разработки веб-приложений в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Отладчик [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] предоставляет мощные средства для локальной отладки веб-приложений [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] или их отладки на удаленном сервере. В этом разделе описывается отладка [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] проекта во время разработки. Сведения об отладке [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] веб-приложение уже установлено на рабочем сервере, см. в разделе [Отладка развернутых веб-приложений](../debugger/debugging-deployed-web-applications.md).  
  
 Чтобы выполнить отладку приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]:  
  
- Необходимо иметь требуемые разрешения. Дополнительные сведения см. в статье [System Requirements](../debugger/aspnet-debugging-system-requirements.md).  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] отладка должна быть включена в **свойства проекта**.  
  
- В файле конфигурации данного приложения (Web.config) необходимо установить режим отладки. В режиме отладки [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] генерирует символы для динамически сгенерированных файлов и включает присоединение отладчика к приложению [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] устанавливает это автоматически при запуске отладки, если проект создан на основе шаблона веб-проектов.  
  
- Дополнительные сведения см. в разделе [Практическое руководство. Включение отладки для приложений ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### <a name="to-debug-a-web-application-during-development"></a>Отладка веб-приложения во время разработки  
  
1. На **Отладка** меню, щелкните **запустить** чтобы начать отладку веб-приложения.  
  
     С помощью [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] выполняется построение проекта веб-приложения, развертывание (если необходимо), запуск сервера разработки ASP.NET при локальной отладке и присоединение к рабочему процессу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
2. Используйте отладчик, чтобы создавать и снимать точки останова, переходить и выполнять другие операции отладки, как и для любого другого приложения.  
  
     Дополнительные сведения см. в разделе [Общие сведения об отладчике](../debugger/debugger-basics.md).  
  
3. На **Отладка** меню, щелкните **остановить отладку** Чтобы остановить сеанс отладки, или на **файл** меню в Internet Explorer, нажмите кнопку **закрыть**.  
  
## <a name="see-also"></a>См. также  
 [Отладка веб-приложений и скриптов](../debugger/debugging-web-applications-and-script.md)   
 [Отладка приложений ASP.NET и AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Практическое руководство. Включение отладки для приложений ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
