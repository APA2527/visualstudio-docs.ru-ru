---
title: DEBUG_ADDRESS_UNION | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fddd1fdc0aef74f637c058cd440f6e8309fe3432
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615296"
---
# <a name="debugaddressunion"></a>DEBUG_ADDRESS_UNION
Описываются различные типы адресов.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>Участники
`dwKind`\
Значение из [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) перечисления, указывающее способ интерпретации объединение.

`addr.addrNative`\
[C++ только] Содержит [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) структуры, если `dwKind` = ADDRESS_KIND_NATIVE.

`addr.addrThisRel`\
[C++ только] Содержит[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) структуры, если `dwKind` = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

`addr.addUPhysical`\
[C++ только] Содержит[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) структуры, если `dwKind` = ADDRESS_KIND_UNMANAGED_PHYSICAL.

`addr.addrMethod`\
[C++ только] Содержит[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) структуры, если `dwKind` = ADDRESS_KIND_METHOD.

`addr.addrField`\
[C++ только] Содержит[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) структуры, если `dwKind` = ADDRESS_KIND_FIELD.

`addr.addrLocal`\
[C++ только] Содержит[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) структуры, если `dwKind` = ADDRESS_KIND_LOCAL.

`addr.addrParam`\
[C++ только] Содержит[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) структуры, если `dwKind` = ADDRESS_KIND_PARAM.

`addr.addrArrayElem`\
[C++ только] Содержит[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) структуры, если `dwKind` = ADDRESS_KIND_ARRAYELEM.

`addr.addrRetVal`\
[C++ только] Содержит[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) структуры, если `dwKind` = ADDRESS_KIND_RETVAL.

`addr.unused`\
[C++ только] padding.

`addr`\
[C++ только] Имя объединения.

`unionmember`\
[C# только] Это значение необходимо выполнить маршалинг в подходящей структурой тип на основе `dwKind`. См. в разделе "Примечания" для ассоциации между `dwKind` и интерпретацию объединения.

## <a name="remarks"></a>Примечания
Эта структура является частью [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структурировать и представляет собой одну из нескольких различных видов адресов ( `DEBUG_ADDRESS` структура заполняется с помощью вызова [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) метод).

 [C# только] В следующей таблице показаны способ интерпретации `unionmember` член для каждого типа адреса. В примере показано, как это можно сделать для одного типа адреса.

|`dwKind`|`unionmember` интерпретируется как|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>Пример
В этом примере показано, как интерпретировать один вид адреса (`METADATA_ADDRESS_ARRAYELEM`) из `DEBUG_ADDRESS_UNION` структуры в C#. Точно так же может интерпретироваться оставшиеся элементы.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
            }
        }
    }
}
```

## <a name="requirements"></a>Требования
Заголовок: sh.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
