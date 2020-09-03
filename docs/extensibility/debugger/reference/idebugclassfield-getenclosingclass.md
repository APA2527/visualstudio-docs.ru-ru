---
title: 'Идебугклассфиелд:: Жетенклосингкласс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5a68e32da370d6881eb2b74cbca157f7b899329
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734391"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Возвращает класс, который заключает в себя этот класс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetEnclosingClass(
    IDebugClassField** ppClassField
);
```

```csharp
int GetEnclosingClass(
    out IDebugClassField ppClassField
);
```

## <a name="parameters"></a>Параметры
`ppClassField`\
заполняет Возвращает объект [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) , представляющий включающий класс. Возвращает значение null, если не существует включающего класса.

## <a name="return-value"></a>Возвращаемое значение
В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
Если класс, представленный этим объектом [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) , является вложенным классом, то `ppClassField` параметр возвращает `IDebugClassField` объект, представляющий включающий класс. Например, с учетом этого определения класса:

```
class RootClass {
    class NestedClass { }
};
```

Вызов `GetEnclosingClass` метода для объекта, `IDebugClassField` представляющего `NestedClass` класс, возвращает объект, `IDebugClassField` представляющий класс `RootClass` .

## <a name="see-also"></a>См. также раздел
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
