---
title: IDebugExpression2::EvaluateSync | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateSync
helpviewer_keywords:
- IDebugExpression2::EvaluateSync
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 602a823e4066aff40d1f6271a20b480bb4a92f5b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158425"
---
# <a name="idebugexpression2evaluatesync"></a>IDebugExpression2::EvaluateSync
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод вычисляет выражение в синхронном режиме.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EvaluateSync(   
   EVALFLAGS             dwFlags,  
   DWORD                 dwTimeout,  
   IDebugEventCallback2* pExprCallback,  
   IDebugProperty2**     ppResult  
);  
```  
  
```csharp  
int EvaluateSync(  
   enum_EVALFLAGS       dwFlags,   
   uint                 dwTimeout,   
   IDebugEventCallback2 pExprCallback,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFlags`  
 [in] Сочетание флагов из [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисление, управлять вычисления выражения.  
  
 `dwTimeout`  
 [in] Максимальное время в миллисекундах для ожидания перед возвратом из этого метода. Используйте `INFINITE` для неограниченного времени ожидания.  
  
 `pExprCallback`  
 [in] Этот параметр всегда является значение null.  
  
 `ppResult`  
 [out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , содержащий результат вычисления выражения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Ниже приведены некоторые коды типичных ошибок.  
  
|Error|Описание|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Сейчас вычисляется другого выражения и вычисление одновременных выражений не поддерживается.|  
|E_EVALUATE_TIMEOUT|Истекло время ожидания оценки.|  
  
## <a name="remarks"></a>Примечания  
 Синхронные вычисления не нужно отправить событие вернитесь в Visual Studio после завершения оценки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простого `CExpression` объект, реализующий [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) интерфейс.  
  
```cpp#  
HRESULT CExpression::EvaluateSync(EVALFLAGS dwFlags,  
                                  DWORD dwTimeout,  
                                  IDebugEventCallback2* pExprCallback,  
                                  IDebugProperty2** ppResult)  
{  
    // Set the aborted state to FALSE.    
    m_bAborted = FALSE;    
    // Delegate the evaluation to EvalExpression.    
    return EvalExpression(TRUE, ppResult);    
}  
  
HRESULT CExpression::EvalExpression(BOOL bSynchronous,  
                                    IDebugProperty2** ppResult)  
{  
    HRESULT hr;  
  
    // Get the value of an environment variable.  
    PCSTR pszVal = m_pEnvBlock->GetEnv(m_pszVarName);  
    // Create and initialize a CEnvVar object with the retrieved value.  
    // CEnvVar implements the IDebugProperty2 interface.  
    CComObject<CEnvVar> *pEnvVar;  
    CComObject<CEnvVar>::CreateInstance(&pEnvVar);  
    pEnvVar->Init(m_pszVarName, pszVal, m_pDoc);  
  
    if (pszVal) {  
        // Check for synchronous evaluation.  
        if (bSynchronous) {  
            // Set and AddRef the result, IDebugProperty2 interface.  
            *ppResult = pEnvVar;  
            (*ppResult)->AddRef();  
            hr = S_OK;  
        } else {  
            //For asynchronous evaluation, send an evaluation complete event.  
            CExprEvalEvent *pExprEvent = new CExprEvalEvent(this, pEnvVar);  
            pExprEvent->SendEvent(m_pExprCallback, NULL, NULL, NULL);  
        }  
    } else {  
        // If a valid value is not retrieved, return E_FAIL.  
        hr = E_FAIL;  
    }  
    return hr;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
