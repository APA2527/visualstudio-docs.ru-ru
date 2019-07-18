---
title: ISimpleConnectionPoint::DescribeEvents | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b5824f945ad25f177fc169b58157377bf53bcce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786423"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Возвращает идентификатор DISPID и имя для каждого события в указанном диапазоне событий.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `iEvent`  
 [in] Индекс первого события для извлечения.  
  
 `cEvents`  
 [in] Количество событий для получения.  
  
 `prgid`  
 [out] Массив значений DISPID событий.  
  
 `prgbstr`  
 [out] Массив имен событий.  
  
 `pcEventsFetched`  
 [out] Фактическое число извлечь события.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`S_FALSE`|Были запрошены дополнительные события, не были доступны. Недоступны события представляются с DISPID_NULL и null BSTR.|  
|`E_INVALIDARG`|Элементы не удалось получить.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает идентификатор DISPID и имя для каждого события в указанном диапазоне событий.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)