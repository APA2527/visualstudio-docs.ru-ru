---
title: Идебугпоинтеробжект::D ереференце | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b3646df80dc93d3248c698efb172bb12a09925e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869639"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Возвращает объект, на который указывает.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DeReference( 
   DWORD          dwIndex,
   IDebugObject** ppObject
);
```

```csharp
int Dereference(
   uint             dwIndex,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Параметры
`dwIndex`\
окне Простое смещение в байтах от начала объекта, на который указывает.

`ppObject`\
заполняет Возвращает объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий объект, на который указывает, а также смещение, если оно есть.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки. Возвращает E_FAIL, если этот объект не указывает на другой объект.

## <a name="remarks"></a>Remarks
 Объект, на который указывает, может быть примитивом или более сложным типом, например классом или структурой.

## <a name="see-also"></a>См. также раздел
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
