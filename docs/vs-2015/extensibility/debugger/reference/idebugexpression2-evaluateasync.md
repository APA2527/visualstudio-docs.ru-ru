---
title: 'IDebugExpression2:: Евалуатеасинк | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e084152f6215878816739f46dc91fa322cf9c94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158441"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод асинхронно вычисляет выражение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```csharp  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFlags`  
 окне Сочетание флагов из перечисления [евалфлагс](../../../extensibility/debugger/reference/evalflags.md) , которое управляет вычислением выражений.  
  
 `pExprCallback`  
 окне Этот параметр всегда имеет значение null.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. Типичный код ошибки:  
  
|Ошибка|Описание|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|В настоящее время выполняется вычисление другого выражения, и одновременная Оценка выражений не поддерживается.|  
  
## <a name="remarks"></a>Remarks  
 Этот метод должен возвращать значение сразу после начала вычисления выражения. Если выражение успешно вычислено, [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) должен быть отправлен в обратный вызов события [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , как это указано с помощью функции [attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) или [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простого `CExpression` объекта, реализующего интерфейс [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) .  
  
```cpp#  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [евалфлагс](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
