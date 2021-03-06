---
title: 'IDebugModule3:: Исусеркоде | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c8b313ecdbc1168238bad517f34350a420fb30ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929775"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Получает сведения о том, представляет ли модуль пользовательский код.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

## <a name="parameters"></a>Параметры
`pfUser`\
заполняет Ненулевое ( `TRUE` ) Если модуль представляет пользовательский код, ноль ( `FALSE` ), если нет.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
