---
title: 'IDebugProperty3:: Креатеобжектид | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d555d7b0480d910a5cb88397db5bfd7e734fd1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896127"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Создает уникальный идентификатор для этого свойства, чтобы убедиться, что он уникален для всех остальных свойств.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод вызывается, когда диспетчер отладки сеанса хочет убедиться, что это свойство однозначно идентифицируется всеми другими свойствами. Модуль отладки (DE) поддерживает этот метод, если только свойства, с которыми он работает, уже определены уникальным образом. Если параметр DE не поддерживает этот метод, он возвращает `E_NOTIMPL` .

 Любой уникальный идентификатор, созданный с помощью `CreateObjectID` , уничтожается при вызове метода [дестройобжектид](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) . Кроме того, он сигнализирует об окончании потребности в уникальном определении этого свойства.

> [!NOTE]
> Не существует метода для получения этого уникального идентификатора, поэтому при вызове метода DE может выполнять любые необходимые действия для уникальных идентификаторов `CreateObjectID` .

## <a name="see-also"></a>См. также раздел
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
