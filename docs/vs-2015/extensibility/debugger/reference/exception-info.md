---
title: EXCEPTION_INFO | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 66af4d95707be99865df3df32751215cf5eb10b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181176"
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Описывает исключение или ошибка времени выполнения, выводится отлаживаемой программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```csharp  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## <a name="members"></a>Участники  
 pProgram  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий программу, в котором произошло исключение.  
  
 bstrProgramName  
 Имя программы, в котором произошло исключение.  
  
 bstrExceptionName  
 Имя исключения.  
  
 dwCode  
 Идентификационный код ошибки исключения или во время выполнения.  
  
 dwState  
 Значение из [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) перечисление, определяющее состояние исключения.  
  
 guidType  
 Идентификатор GUID языка, либо `guidLang` или `guidEng`.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается в качестве параметра [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) и [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) методы. Эта структура также передается [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) метод для заполнения.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
