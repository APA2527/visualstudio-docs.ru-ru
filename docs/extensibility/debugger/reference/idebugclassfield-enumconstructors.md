---
title: IDebugClassField::EnumConstructors | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb31af11ae4ecc2618e577df6e3b1e2e45a0cbc7
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203217"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Создает перечислитель для конструкторов для данного класса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Параметры
`cMatch`\
[in] Значение из [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) перечисления, указывающее тип конструкторов для перечисления.

`ppEnum`\
[out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список конструкторов. Возвращает значение null, если конструкторы отсутствуют.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK, или возвращает S_FALSE, если конструкторы отсутствуют. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Каждый элемент перечисления является [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) объект, описывающий метод-конструктор.

 Список конструкторов обычно не включает конструкторы по умолчанию, предоставленные с помощью компилятора.

## <a name="see-also"></a>См. также
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)