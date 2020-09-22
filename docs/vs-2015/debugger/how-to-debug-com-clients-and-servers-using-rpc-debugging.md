---
title: Инструкции. отладка клиентов и серверов COM с помощью отладки RPC | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fda2a10cd559f940ab87e5cc8c26f5b47dbec194
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843358"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Практическое руководство. Отладка клиентов и серверов COM с помощью отладки RPC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для отладки клиент-серверных приложений COM можно использовать отладку удаленного вызова процедур (RPC). Для этого необходимо включить отладку RPC. Если отладка RPC включена, то при заходе в вызов сервера со стороны клиента отладчик подключается к серверу, позволяя выполнить отладку кода. Когда отладчик подключен, все его возможности можно использовать для отладки процессов как на стороне сервера, так и на стороне клиента.  
  
### <a name="to-enable-rpc-debugging"></a>Включение отладки RPC  
  
1. В меню **Сервис** выберите команду **Параметры**.  
  
2. В диалоговом окне **Параметры** щелкните папку **Отладка**.  
  
3. Щелкните страницу **Машинный код**.  
  
4. Установите флажок **Отладка RPC**.  
  
    > [!NOTE]
    > Для отладки вызовов RPC необходимо иметь привилегии администратора или опытного пользователя.  
  
    > [!NOTE]
    > Выполнение удаленных вызовов процедур с заходом на удаленный сервер под управлением Microsoft Windows Vista будет работать только в том случае, если к удаленному серверу подключен отладчик машинного кода. В противном случае вызов RPC завершится сбоем без сообщения об ошибке. Или же вызов RPC будет выполнен, но пошаговое выполнение вызова RPC не будет работать.  
  
## <a name="see-also"></a>См. также:  
 [Отладка сервера и контейнеров COM](../debugger/com-server-and-container-debugging.md)   
 [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)
