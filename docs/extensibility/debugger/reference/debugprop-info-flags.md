---
title: DEBUGPROP_INFO_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae512bec8f88be81a0c45ddf541c94d78b483284
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318374"
---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
Указывает, какую информацию нужно извлечь сведения об объекте debug свойство.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
typedef DWORD DEBUGPROP_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
```

## <a name="fields"></a>Поля
`DEBUGPROP_INFO_FULLNAME`\
Инициализация и использование `bstrFullName` поля.

`DEBUGPROP_INFO_NAME`\
Инициализация и использование `bstrName` поля.

`DEBUGPROP_INFO_TYPE`\
Инициализация и использование `bstrType` поля.

`DEBUGPROP_INFO_VALUE`\
Инициализация и использование `bstrValue` поля.

`DEBUGPROP_INFO_ATTRIB`\
Инициализация и использование `dwAttrib` поля.

`DEBUGPROP_INFO_PROP`\
Инициализация и использование `pProperty` поле, содержащее [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) интерфейс.

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Указывает, что поле значения должен содержать значение развернутый автоматически, если он доступен для этого типа объектов.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Не рекомендуется.

`DEBUGPROP_INFO_VALUE_RAW`\
Не возвращают значений гибко и членов (то есть не форматировать значения).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Не возвращают все особые Синтезированная значения (например, не следует вызывать `ToString()` объекта для получения значения).

`DEBUGPROP_INFO_NONE`\
Указывает, что флаги не установлены.

`DEBUGPROP_INFO_STANDARD`\
Инициализация и использование `dwAttrib`, `bstrName`, `bstrType`, и `bstrValue` поля.

`DEBUGPROP_INFO_All`\
Указывает маску всех флагов.

## <a name="remarks"></a>Примечания
Эти значения передаются [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), и [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) методы, чтобы указать, какие поля должны быть инициализированы [ DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры.

Эти значения также используются для `dwFields` членом `DEBUG_PROPERTY_INFO` структуры для указания поля структуры, используемые и допустимым при возвращении структуры.

Эти значения могут объединяться с побитовым объектом `OR`.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
