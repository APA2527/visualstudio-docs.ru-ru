---
title: JMC_CODE_SPEC | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0a6746ed0df400efc7feb3fb541c57c88f78cc2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714744"
---
# <a name="jmc_code_spec"></a>JMC_CODE_SPEC
Эта структура используется для задания сведений Жустмикоде для модуля.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _JMC_CODE_SPEC {
    BOOL fIsUserCode;
    BSTR bstrModuleName;
} JMC_CODE_SPEC;
```

```csharp
public struct JMC_CODE_SPEC {
    public int    fIsUserCode;
    public string bstrModuleName;
};
```

## <a name="members"></a>Участники
`fIsUserCode`\
Ненулевое значение ( `TRUE` ), если модуль должен считаться пользовательским кодом; в противном случае — нуль ( `FALSE` ), если модуль должен обрабатываться как внешний код, а не для отладки.

`bstrModuleName`\
Имя рассматриваемого модуля.

## <a name="remarks"></a>Remarks
Эта структура передается в качестве списка таких структур в метод [сетжустмикодестате](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)
