---
title: Интерфейс IDebugSessionProvider | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe73901d92cb42675ff9ec981bd9b90dcca5d546
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979052"
---
# <a name="idebugsessionprovider-interface"></a>Интерфейс IDebugSessionProvider
Основной интерфейс, предоставленный с помощью отладчика интегрированной среды разработки для реализации узлов и языка инициировать отладки. Он устанавливает сеанс отладки для запущенного приложения. Этот интерфейс реализуется диспетчером отладки.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugSessionProvider` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Инициирует сеанс отладки с указанным приложением.|