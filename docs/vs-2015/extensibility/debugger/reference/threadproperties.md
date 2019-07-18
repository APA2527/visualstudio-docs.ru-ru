---
title: THREADPROPERTIES | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4815a1e42b98fba812e8a3c2a53516bff16081db
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204824"
---
# <a name="threadproperties"></a>THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Описывает свойства потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```csharp  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## <a name="members"></a>Участники  
 dwFields  
 Сочетание флагов из [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) перечисление, описывающее, какие поля в этой структуре являются допустимыми.  
  
 dwThreadId  
 Идентификатор потока.  
  
 dwSuspendCount  
 Число приостановок потока.  
  
 dwThreadState  
 Значение из [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) перечисление, указывающее состояние работы потока.  
  
 bstrPriority  
 Строка, указывающая приоритет потока; Например «Выше среднего», «Normal» или «Critical времени».  
  
 bstName  
 Имя потока.  
  
 bstrLocation  
 Расположение потока (обычно верхний кадр стека), обычно выраженное как имя метода, где выполнение приостановлено.  
  
## <a name="remarks"></a>Примечания  
 Эта структура заполняется с помощью вызова [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) метод. Сведения, поэтому возвращаемые обычно используется при заполнении **потоков** окна.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
