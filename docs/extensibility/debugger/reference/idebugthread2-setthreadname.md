---
title: IDebugThread2::SetThreadName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetThreadName
helpviewer_keywords:
- IDebugThread2::SetThreadName
ms.assetid: fa934121-3f58-44dc-9c30-d3f752e44c8b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94a9cde9f757194a51a15e2513260f7e8e3fd490
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199476"
---
# <a name="idebugthread2setthreadname"></a>IDebugThread2::SetThreadName
Задает имя потока.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetThreadName ( 
   LPCOLESTR pszName
);
```

```csharp
int SetThreadName ( 
   string pszName
);
```

## <a name="parameters"></a>Параметры
`pszName`\
[in] Имя потока.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Чтобы получить имя потока, вызовите [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md) метод.

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)