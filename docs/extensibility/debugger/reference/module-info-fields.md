---
title: MODULE_INFO_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dba231f173f3828243e284a7d68a877204df1bd0
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458022"
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
Задает флаги для отладки модуля.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
typedef DWORD MODULE_INFO_FIELDS;
```

```csharp
public enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
```

## <a name="fields"></a>Поля
 `MIF_NONE`\
 Инициализировать или использовать ни одно из полей в структуре.

 `MIF_NAME`\
 Инициализация и использование `m_bstrName` в [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) структуры.

 `MIF_URL`\
 Инициализация и использование `m_bstrUrl` в `MODULE_INFO` структуры.

 `MIF_VERSION`\
 Инициализация и использование `m_bstrVersion` в `MODULE_INFO` структуры.

 `MIF_DEBUGMESSAGE`\
 Инициализация и использование `m_bstrDebugMessage` в `MODULE_INFO` структуры.

 `MIF_LOADADDRESS`\
 Инициализация и использование `m_addrLoadAddress` в `MODULE_INFO` структуры.

 `MIF_PREFFEREDADDRESS`\
 Инициализация и использование `m_addrPreferredLoadAddress` в `MODULE_INFO` структуры.

 `MIF_SIZE`\
 Инициализация и использование `m_dwSize` в `MODULE_INFO` структуры.

 `MIF_LOADORDER`\
 Инициализация и использование `m_dwLoadOrder` в `MODULE_INFO` структуры.

 `MIF_TIMESTAMP`\
 Инициализация и использование `m_TimeStamp` в `MODULE_INFO` структуры.

 `MIF_URLSYMBOLLOCATION`\
 Инициализация и использование `m_bstrUrlSymbolLocation` в `MODULE_INFO` структуры.

 `MIF_FLAGS`\
 Инициализация и использование `m_dwModuleFlags` в `MODULE_INFO` структуры.

 `MIF_ALLFIELDS`\
 Инициализация и использование всех полей в `MODULE_INFO` структуры.

## <a name="remarks"></a>Примечания
 Эти значения передаются в качестве аргумента [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) метод, чтобы указать, какие поля [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) структуры должны быть инициализированы.

 Эти значения также используются в `MODULE_INFO` структура указывает, какие поля используются и допустимым.

 Эти флаги могут быть объединены с побитовым объектом `OR`.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)