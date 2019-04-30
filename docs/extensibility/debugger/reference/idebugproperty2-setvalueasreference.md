---
title: IDebugProperty2::SetValueAsReference | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2c8baa009160cc22766d1a30711fae5b153d2c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869446"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Задает значение этого свойства к значению данной ссылки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetValueAsReference(
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```csharp
int SetValueAsReference(
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

#### <a name="parameters"></a>Параметры
 `rgpArgs`

 [in] Массив аргументов для передачи методу задания свойства управляемого кода. Если метод задания свойства не принимает аргументы или если данный [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объект не ссылается на таких метода задания свойства, `rgpArgs` должен иметь значение null. Этот параметр обычно является значение null.

 `dwArgCount`

 [in] Число аргументов в `rgpArgs` массива.

 `pValue`

 [in] Ссылка, в виде [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объекта, чтобы значение, используемое для задания этого свойства.

 `dwTimeout`

 [in] Как долго следует использовать для задания значения, в миллисекундах. Стандартное значение — `INFINITE`. Это влияет на продолжительность времени, который может принимать любые возможные оценки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает ошибку, код, обычно один из следующих:

|Error|Описание|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Значение из ссылки не поддерживается.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Невозможно задать значение, так как оно ссылается на метод.|
|`E_SETVALUE_VALUE_IS_READONLY`|Значение только для чтения и не может быть задано.|
|`E_NOTIMPL`|Метод не реализован.|

## <a name="see-also"></a>См. также
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)