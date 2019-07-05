---
title: IApplicationDebugger::onHandleBreakPoint | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onHandleBreakPoint
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onHandleBreakPoint
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edf8816cd646596ce1f897dfd9d949790d52b7b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991353"
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
Обрабатывает событие точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `prpt`  
 [in] Поток, где произошло точки останова.  
  
 `br`  
 [in] Причина для точки останова.  
  
 `pError`  
 [in] Сведения об ошибке среды выполнения, предоставляемых при значение `br` является BREAKREASON_ERROR.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается при достижении точки останова и `IDebugApplication::HandleBreakPoint` вызывается.  
  
 Приложение будет отложен до интегрированной среды разработки, он вызывает `IRemoteDebugApplication::ResumeFromBreakPoint`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [Перечисление BREAKREASON](../../winscript/reference/breakreason-enumeration.md)