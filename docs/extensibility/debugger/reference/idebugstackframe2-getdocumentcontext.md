---
title: 'IDebugStackFrame2:: Жетдокументконтекст | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetDocumentContext
helpviewer_keywords:
- IDebugStackFrame2::GetDocumentContext
ms.assetid: 69e81439-1238-4f18-9028-6fd1c1ba5e4a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8de85f157995db77653b71f7b25f3106caffb9ed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837516"
---
# <a name="idebugstackframe2getdocumentcontext"></a>IDebugStackFrame2::GetDocumentContext
Возвращает контекст документа для этого кадра стека.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppCxt
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppCxt
);
```

## <a name="parameters"></a>Параметры
`ppCxt`\
заполняет Возвращает объект [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , представляющий текущую точку в исходном документе.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод выполняется быстрее, чем вызов метода [жеткодеконтекст](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) и последующий вызов метода [жетдокументконтекст](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) в контексте кода. Однако не гарантируется, что каждый модуль отладки (DE) будет реализовывать этот метод.

## <a name="see-also"></a>См. также раздел
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
