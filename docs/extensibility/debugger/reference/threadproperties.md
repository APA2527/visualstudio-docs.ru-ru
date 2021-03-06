---
title: СРЕАДПРОПЕРТИЕС | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a2eb7abf897cf4891f08228dd5f0c918f580a1ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850665"
---
# <a name="threadproperties"></a>THREADPROPERTIES
Описывает свойства потока.

## <a name="syntax"></a>Синтаксис

```cpp
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

## <a name="members"></a>Члены
 `dwFields`\
 Сочетание флагов из перечисления [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) , описывающее, какие поля в этой структуре являются допустимыми.

 `dwThreadId`\
 Идентификатор потока.

 `dwSuspendCount`\
 Число приостановок потока.

 `dwThreadState`\
 Значение из перечисления "перечисление [", указывающее](../../../extensibility/debugger/reference/threadstate.md) состояние операционного потока.

 `bstrPriority`\
 Строка, указывающая приоритет потока; Например, "выше обычного", "нормального" или "критическое время".

 `bstName`\
 Имя потока.

 `bstrLocation`\
 Расположение потока (обычно самый верхний кадр стека), обычно выраженное в виде имени метода, в котором выполнение в данный момент останавливается.

## <a name="remarks"></a>Remarks
 Эта структура заполняется вызовом метода [жетсреадпропертиес](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) . Эти сведения обычно используются при заполнении окна **потоков** .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
