---
title: BUILT_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35ae5661127c0e19e87c96a47a2985161beae7c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874386"
---
# <a name="built_type"></a>BUILT_TYPE
Эта структура задает сведения о типе поля, взятого из метаданных.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagTYPE_BUILT {
    ULONG32      ulAppDomainID;
    GUID         guidModule;
    IDebugField* pUnderlyingField;
} BUILT_TYPE;
```

```csharp
public struct BUILT_TYPE {
    public uint        ulAppDomainID;
    public Guid        guidModule;
    public IDebugField pUnderlyingField;
};
```

## <a name="members"></a>Члены
`ulAppDomainID`\
Идентификатор приложения, от которого получен символ. Используется для уникальной идентификации экземпляра приложения.

`guidModule`\
Идентификатор GUID модуля, содержащего это поле.

`pUnderlyingField`\
Объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , определяющий базовое поле, связанное с этим построенным полем.

## <a name="remarks"></a>Remarks
Эта структура отображается как часть объединения в структуре [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) , если `dwKind` поле `TYPE_INFO` структуры имеет `TYPE_KIND_BUILT` значение (Value из перечисления [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).

## <a name="requirements"></a>Требования
Заголовок: sh. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
