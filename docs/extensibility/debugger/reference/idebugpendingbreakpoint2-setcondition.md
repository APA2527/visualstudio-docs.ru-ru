---
title: IDebugPendingBreakpoint2::SetCondition | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4a67286b4732436c2a680e13e90740ca9faff299
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842767"
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
Задает или изменяет условие, связанное с ожидающая точка останова.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   BP_CONDITION bpCondition
);
```

#### <a name="parameters"></a>Параметры
 `bpCondition`

 [in] Объект [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) структура, задающая условие для установки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Любое условие, который был ранее связан с ожидающая точка останова будет потеряно. Все точки останова, привязанный из этого ожидающих точек останова, называются присвоено значение, указанное в их условие `bpCondition` параметра.

## <a name="see-also"></a>См. также
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)