---
title: 'Идебугбиндер:: Жетмемориконтекст | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d50126e26b836f7b53ee1abeb5c4988b74a2eed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735996"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
Этот метод преобразует расположение объекта или адрес памяти в контекст памяти.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMemoryContext( 
   IDebugField*           pField,
   DWORD                  dwConstant,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int GetMemoryContext(
   IDebugField              pField,
   uint                     dwConstant,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Параметры
`pField`\
окне Объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , описывающий объект для размещения. Если значение равно `NULL` , используйте `dwConstant` вместо него.

`dwConstant`\
окне Постоянный адрес памяти, например 0x5000.

`ppMemCxt`\
заполняет Возвращает интерфейс [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , представляющий адрес объекта или адрес в памяти.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
