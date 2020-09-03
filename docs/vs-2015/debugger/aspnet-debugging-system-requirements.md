---
title: 'Отладка ASP.NET: Требования к системе | Документация Майкрософт'
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
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aa8951be6da4d77ffb51b6bc8f09a796b373a944
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "67826262"
---
# <a name="aspnet-debugging-system-requirements"></a>Отладка ASP.NET: Требования к системе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе описаны требования к программному обеспечению и безопасности для сценариев локальной и удаленной отладки [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] .  
  
- При локальной отладке [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и веб-приложение выполняются на одном и том же компьютере. Существуют две версии этого сценария:  
  
  - код [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] располагается в файловой системе;  

  - код [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] располагается на веб-сайте служб IIS.  
  
- При удаленной отладке [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] выполняется на клиентском компьютере и используется для отладки веб-приложения, работающего на удаленном (серверном) компьютере.  
  
## <a name="security-requirements"></a>Требования безопасности  
 Для удаленной отладки локальный и удаленный компьютеры должны входить в домен или рабочую группу.  
  
 Чтобы выполнить отладку рабочего процесса [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , необходимо иметь разрешение на отладку этого процесса. По умолчанию приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] выполняются от имени учетной записи пользователя **ASPNET** . Если рабочий процесс выполняется от имени учетной записи **ASPNET**или **NETWORK SERVICE**, для его отладки необходимо иметь права администратора.  
  
 Имя рабочего процесса [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] варьируется в зависимости от сценария отладки и версии служб IIS. Дополнительные сведения см. в разделе [Практическое руководство. найти имя процесса ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Вы можете изменить учетную запись пользователя, от имени которой должен выполняться рабочий процесс [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Для этого следует внести соответствующие изменения в файл machine.config на сервере, на котором запускаются службы IIS. Оптимальный способ сделать это — с помощью **Диспетчера служб IIS**. Дополнительные сведения см. в разделе [Практическое руководство. выполнить рабочий процесс с учетной записью пользователя](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Если в качестве учетной записи, от имени которой должен запускаться рабочий процесс [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , указать собственную учетную запись, то обладать правами администратора на сервере, на котором работают службы IIS, не потребуется.  
  
> [!CAUTION]
> Прежде чем запускать рабочий процесс [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] от имени другой учетной записи, проанализируйте последствия возможной вредоносной атаки на рабочий процесс [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] при его выполнении от имени этой учетной записи. Учетные записи ASPNET и NETWORK SERVICE обладают минимальным набором разрешений, минимизируя возможный вред в случае вредоносной атаки на процесс. При выполнении рабочего процесса [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] от имени учетной записи с более широким объемом прав объем возможного вреда возрастает.  
  
## <a name="see-also"></a>См. также:  
 [Отладка приложений ASP.NET и AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Практическое руководство. Выполнение рабочего процесса с учетной записью пользователя](../debugger/how-to-run-the-worker-process-under-a-user-account.md)
