---
title: 'Иенумдебугфиелдс:: Reset | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1cbe3ecaf681a0fb88dab46b9c2dac2110b7beb4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919687"
---
# <a name="ienumdebugfieldsreset"></a>IEnumDebugFields::Reset
Этот метод сбрасывает перечисление к первому элементу.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

#### <a name="parameters"></a>Параметры
 Отсутствуют

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 После вызова этого метода следующий вызов [Next](../../../extensibility/debugger/reference/ienumdebugfields-next.md) возвращает первый элемент перечисления.

## <a name="see-also"></a>См. также раздел
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [Вперед](../../../extensibility/debugger/reference/ienumdebugfields-next.md)
