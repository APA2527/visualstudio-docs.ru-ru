---
title: IDebugClassField::GetEnclosingClass | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6927a63241e2f2794fb5c70945962e00a1676431
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329500"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Возвращает класс, который содержит этот класс.

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
[out] Возвращает [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) объект, представляющий включающий класс. Возвращает значение null, если нет включающего класса.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
Если класс, представленный это [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) объекта является вложенным классом, а затем `ppClassField` параметр возвращает `IDebugClassField` объект, представляющий включающий класс. Например рассмотрим следующее определение класса:

```
class RootClass {
    class NestedClass { }
};
```

Вызов `GetEnclosingClass` метод `IDebugClassField` объект, представляющий `NestedClass` возвращает `IDebugClassField` объект, представляющий класс `RootClass`.

## <a name="see-also"></a>См. также
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
