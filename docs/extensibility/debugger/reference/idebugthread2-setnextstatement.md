---
title: 'IDebugThread2:: Сетнекстстатемент | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c8a7aff8c6e902b20c5569e2553aececae835ad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893715"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Задает текущий указатель инструкции для данного контекста кода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int SetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>Параметры
`pStackFrame`\
Зарезервировано для будущего использования; Задайте для значение null.

`pCodeContext`\
окне Объект [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , описывающий расположение кода для выполнения и его контекст.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. В следующей таблице показаны другие возможные значения.

|Значение|Описание|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|Следующий оператор не может находиться в кадре стека более глубоко в стеке кадров.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|Следующая инструкция не связана ни с одним кадром в стеке.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Некоторые отладчики отладчика не могут задать следующий оператор после исключения.|

## <a name="remarks"></a>Remarks
 Указатель инструкции указывает следующую инструкцию или инструкцию для выполнения. Этот метод используется для повтора строки исходного кода или принудительного выполнения, чтобы продолжить выполнение в другой функции, например.

## <a name="see-also"></a>См. также раздел
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
