---
title: 'Идебуженумфиелд:: Жетстрингфромвалуе | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 03c2ab7b701163e22a5cc3ff386f447c5199ff15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892571"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Этот метод получает имя константы перечисления, учитывая его значение.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetStringFromValue(
   ULONGLONG value,
   BSTR*     pbstrValue
);
```

```csharp
int GetStringFromValue(
   ulong      value,
   out string pbstrValue
);
```

## <a name="parameters"></a>Параметры
`value`\
окне Значение, для которого необходимо получить имя константы перечисления.

`pbstrValue`\
заполняет Возвращает имя константы перечисления.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает, `S_FALSE` Если значение не имеет связанного имени, или возвращает код ошибки.

## <a name="remarks"></a>Remarks
 При наличии нескольких имен, связанных с одним и тем же значением, будет возвращено первое имя, определенное в перечислении.

## <a name="see-also"></a>См. также раздел
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
