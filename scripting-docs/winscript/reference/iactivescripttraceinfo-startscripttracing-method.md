---
title: Метод IActiveScriptTraceInfo::StartScriptTracing | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b87971e1fd2e484aa54ff4de56ee56e00b19b1e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991196"
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>Метод IActiveScriptTraceInfo::StartScriptTracing
Запускает трассировку сценария.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>Параметры  
 `pSiteTraceInfo`  
 Указатель на IActiveScriptSiteTraceInfo главного приложения.  
  
 `guidContextId`  
 Идентификатор GUID контекста.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Ниже перечислены возможные возвращаемые значения для этого метода.  
  
1. ЗНАЧЕНИЕ S_OK: Выполнено.  
  
2. E_POINTER: `pSiteTraceInfo` является указателем NULL.  
  
3. E_NOTIMPL: Не реализовано.