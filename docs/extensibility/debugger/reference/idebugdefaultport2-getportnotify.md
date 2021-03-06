---
title: 'IDebugDefaultPort2:: Жетпортнотифи | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26e269e37eddf37aafb87c9e479feb0047bfce70
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934309"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Этот метод получает интерфейс [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) для этого порта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>Параметры
`ppPortNotify`\
заполняет Объект [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Как правило, `QueryInterface` метод вызывается для объекта, реализующего интерфейс [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , чтобы получить интерфейс [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) . Однако существуют обстоятельства, в которых требуемый интерфейс реализуется на другом объекте. Этот метод скрывает эти обстоятельства и возвращает `IDebugPortNotify2` интерфейс из наиболее подходящего объекта.

## <a name="see-also"></a>См. также раздел
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
