---
title: BP_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ff3730d3903b71db78c8ecbc025bfe44d6e37f7f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853036"
---
# <a name="bp_flags"></a>BP_FLAGS
Предоставляет необязательные флаги, которые можно использовать для указания дополнительных сведений при задании точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>Поля
`BP_FLAG_NONE`\
Указывает отсутствие флага точки останова.

`BP_FLAG_MAP_DOCPOSITION`\
Указывает, что модуль отладки (DE) должен сопоставлять точку останова с позицией документа. Это применимо только к точкам останова, заданным в исходных файлах, ориентированных на скрипт, например Active Server Pages (ASP).

`BP_FLAG_DONT_STOP`\
Указывает, что точка останова должна обрабатываться модулем отладки, но в конечном итоге отладчик не должен останавливаться (то есть объект события [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) не должен отправляться). Этот флаг предназначен для использования в основном с точками трассировки.

## <a name="remarks"></a>Remarks
Используется для `dwFlags` элемента структур [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

Эти значения можно объединить с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
