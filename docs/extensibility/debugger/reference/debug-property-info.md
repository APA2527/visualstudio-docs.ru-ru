---
title: DEBUG_PROPERTY_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7804cfad48d5029e16619b5ae524fa6e761f11b4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346181"
---
# <a name="debugpropertyinfo"></a>DEBUG_PROPERTY_INFO
Содержит сведения о свойстве отладки.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagDEBUG_PROPERTY_INFO {
    DEBUGPROP_INFO_FLAGS dwValidFields;
    BSTR                 bstrFullName;
    BSTR                 bstrName;
    BSTR                 bstrType;
    BSTR                 bstrValue;
    IDebugProperty2*     pProperty;
    DBG_ATTRIB_FLAGS     dwAttrib;
} DEBUG_PROPERTY_INFO;
```

```csharp
public struct DEBUG_PROPERTY_INFO {
    public uint            dwValidFields;
    public string          bstrFullName;
    public string          bstrName;
    public string          bstrType;
    public string          bstrValue;
    public IDebugProperty2 pProperty;
    public ulong           dwAttrib;
};
```

## <a name="members"></a>Участники
`dwValidFields`\
Сочетание флагов из [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) перечисление, указывающее, какие поля заполнены.

`bstrFullName`\
Полное имя свойства.

`bstrName`\
Имя свойства в контексте.

`bstrType`\
Тип свойства как отформатированную строку.

`bstrValue`\
Значение свойства как отформатированную строку.

`pProperty`\
[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объекта, описанного этой структурой.

`dwAttrib`\
Сочетание флагов из [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) перечисление, описывающее атрибуты данного свойства.

## <a name="remarks"></a>Примечания
Свойство является объектом иерархическую сущность, которая имеет имя, тип и значение. Например свойство можно описать, локальные переменные, параметры, переменные контрольных значений и выражений и регистров.

Эта структура передается [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод, где он заполняется. Эта структура также возвращается как часть списка этой структуры из [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) интерфейс, который, в свою очередь, возвращается из вызова [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) и [ EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) методы.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
