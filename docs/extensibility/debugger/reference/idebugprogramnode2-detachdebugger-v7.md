---
title: IDebugProgramNode2::DetachDebugger_V7 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 241db5db55897932120b3253ff5185cb852ea77b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351208"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> РЕКОМЕНДУЕТСЯ К ИСПОЛЬЗОВАНИЮ. НЕ ИСПОЛЬЗУЙТЕ.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Возвращаемое значение

Реализация всегда должны возвращать `E_NOTIMPL`.

## <a name="remarks"></a>Примечания

> [!WARNING]
> Начиная с Visual Studio 2005, этот метод больше не используется и всегда должны возвращать `E_NOTIMPL`.

Этот метод вызывается, когда отладчик неожиданно завершает работу. При вызове этого метода, DE следует возобновить программы, как если бы, если пользователь отсоединены от него. Следует отправлять дальнейшие события отладки. Программа должна находиться в состоянии там, где это присоединяемого элемента из другой экземпляр отладчика.

## <a name="see-also"></a>См. также

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)