---
title: Интерфейс IDebugSessionProviderEx | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9bf341adeaeb17c8986b1b30b12f58113aef562
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979000"
---
# <a name="idebugsessionproviderex-interface"></a>Интерфейс IDebugSessionProviderEx
Основной интерфейс, предоставляемый с помощью отладчика интегрированной среды разработки для отладки узла и инициирован языка. Он устанавливает сеанс отладки для запущенного приложения. Этот интерфейс реализуется диспетчера отладки.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugSessionProviderEx` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Определяет, возможна ли отладка Just In Time с указанным приложением.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Инициирует сеанс отладки с указанным приложением.|