---
title: IDebugEngine2::D Естройпрограм | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 485875f2ca4cd54c41d959ffaf769368db265243
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879050"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Информирует модуль отладки (DE) о том, что указанная программа была необычным прекращена и что DE должен очистить все ссылки на программу и отправить событие уничтожения программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DestroyProgram( 
   IDebugProgram2* pProgram
);
```

```cpp
int DestroyProgram( 
   IDebugProgram2 pProgram
);
```

## <a name="parameters"></a>Параметры
`pProgram`\
окне Объект [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий программу, которая была нетипично прервана.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 После вызова этого метода метод DE отправляет событие [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) обратно в Диспетчер отладки сеансов (SDM).

 Этот метод не реализуется (Возвращает значение `E_NOTIMPL` ), если процесс de выполняется в том же процессе, что и отлаживаемая программа. Этот метод реализуется только в том случае, если процесс DE выполняется в том же процессе, что и модель SDM.

## <a name="see-also"></a>См. также раздел
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
