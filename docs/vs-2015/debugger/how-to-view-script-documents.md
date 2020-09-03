---
title: Практическое руководство. Просмотр документов скриптов | Документация Майкрософт
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
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 88f923ab0447f1ac7d57e84d94f0ab442d912d67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189591"
---
# <a name="how-to-view-script-documents"></a>Практическое руководство. Просмотр документов скриптов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В более ранних версиях [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] клиентские файлы скриптов, созданные из серверных скриптов, появлялись в окне обозревателя скриптов. Окно обозревателя скриптов часто было скрыто, так что доступность клиентского скрипта была не всегда очевидна.  
  
 В [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] файлы клиентских скриптов, созданные из серверных скриптов, отображаются в обозревателе решений, который по умолчанию отображается. Окно обозревателя скриптов больше не используется.  
  
 Клиентские файлы скриптов отображаются только в режиме отладки или режиме приостановки. Они отображаются в узле **Документы скриптов**.  
  
 Серверные файлы скриптов отображаются всегда. Они отображаются в **\<Website Pathname>** узле. Имя узла напоминает следующий пример: `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Просмотр документа серверного скрипта  
  
1. В **обозревателе решений** откройте узел **\<Website Pathname>** .  
  
2. Дважды щелкните имя файла скрипта, который нужно просмотреть.  
  
     Серверная часть скрипта откроется в окне исходного кода.  
  
### <a name="to-view-a-client-side-script-document"></a>Просмотр документа клиентского скрипта  
  
1. В **Обозревателе решений** откройте узел **Документы скриптов**.  
  
2. Дважды щелкните имя файла скрипта, который нужно просмотреть.  
  
     Клиентская часть скрипта откроется в окне исходного кода.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)
