---
title: IDebugManagedObject::SetFromManagedObject | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dbaaf27222754d4a68d7de6367a2c0d7a1a8be73
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210629"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Задает значение экземпляра класса объекта значения из экземпляра класса значение в качестве параметра указано.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetFromManagedObject( 
   IUnknown* pManagedObject
);
```

```csharp
int SetFromManagedObject(
   object pManagedObject
);
```

## <a name="parameters"></a>Параметры
`pManagedObject`\
[in] Интерфейс, который представляет управляемый объект, содержащий новое значение.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод используется для изменения управляемый объект, представленный [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) объекта.

## <a name="see-also"></a>См. также
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)