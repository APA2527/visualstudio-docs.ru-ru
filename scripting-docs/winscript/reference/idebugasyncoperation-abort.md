---
title: IDebugAsyncOperation::Abort | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Abort
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be696f852f7038316141415494920c43580738c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822103"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Отменяет операцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|S_OK|Метод успешно выполнен.|  
|E_NOTIMPL|Операции не может быть отменено.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод обычно вызывается из потока отладчика, отвечать на запросы отмены. Этот метод вызывает `InProgressAbort` метод `IDebugSyncOperation` вызов объекта.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)