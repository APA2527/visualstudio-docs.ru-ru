---
title: 'Идебужекстендедфиелд:: Исклоседтипе | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4524d7c899480518e669f1f77a4756a83e0cf52f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729051"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Определяет, представляет ли поле закрытый тип.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsClosedType(
   void
);
```

```csharp
int IsClosedType();
```

## <a name="return-value"></a>Возвращаемое значение
 Если поле является закрытым типом, возвращает `S_OK` ; в противном случае возвращает `S_FALSE` .

## <a name="see-also"></a>См. также раздел
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
