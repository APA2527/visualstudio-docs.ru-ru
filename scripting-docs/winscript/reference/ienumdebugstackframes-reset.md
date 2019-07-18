---
title: IEnumDebugStackFrames::Reset | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Reset
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Reset
ms.assetid: 57be2683-5346-4464-bdf5-6fd45b56253a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76cb09ef9456f0dccf3bd034914c9988dd0ff187
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963342"
---
# <a name="ienumdebugstackframesreset"></a>IEnumDebugStackFrames::Reset
Сбрасывает последовательность перечислений в начало.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод сбрасывает последовательность перечислений в начало.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)