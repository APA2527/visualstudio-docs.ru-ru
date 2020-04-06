---
title: BP_RESOLUTION_DATA Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93a78f84c10af047e596459b68211b885d3c3085
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737837"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
Описывает результат связывания точки разрыва данных.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _BP_RESOLUTION_DATA {
    BSTR              bstrDataExpr;
    BSTR              bstrFunc;
    BSTR              bstrImage;
    BP_RES_DATA_FLAGS dwFlags;
} BP_RESOLUTION_DATA;
```

```csharp
public struct BP_RESOLUTION_DATA {
    public string bstrDataExpr;
    public string bstrFunc;
    public string bstrImage;
    public uint   dwFlags;
};
```

## <a name="members"></a>Участники
`bstrDataExpr`\
Выражение данных, которое было связано.

`bstrFunc`\
Имя функции, в ней связана точка разрыва данных (если таковое имеется).

`bstrImage`\
Название модуля (MyModule.dll, например), что точка разрыва данных связана дюйма

`dwFlags`\
Значение из [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) перечисления, описывающее, как реализуется точка разрыва данных.

## <a name="remarks"></a>Примечания
Эта структура является членом [структуры BP_RESOLUTION_LOCATION,](../../../extensibility/debugger/reference/bp-resolution-location.md) которая, в свою очередь, является членом [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) структуры, возвращенной методом [GetResolutionInfo.](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
