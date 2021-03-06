---
title: 'IDebugCodeContext2:: Жетдокументконтекст | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eaac527149d3224370f04d9dec46123b59568ac1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928748"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Возвращает контекст документа, соответствующий данному контексту кода. Контекст документа представляет собой расположение в исходном файле, соответствующее исходному коду, вызвавшему эту инструкцию.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDocumentContext( 
   IDebugDocumentContext2** ppSrcCxt
);
```

```csharp
int GetDocumentContext( 
   out IDebugDocumentContext2 ppSrcCxt
);
```

## <a name="parameters"></a>Параметры
`ppSrcCxt`\
заполняет Возвращает объект [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) , соответствующий контексту кода. Если `S_OK` возвращается значение, этого не должно быть `null` .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Модуль отладки должен возвращать код сбоя, например, если `E_FAIL` в `out` `null` контексте кода нет связанной с исходным положением.

## <a name="remarks"></a>Remarks
 Как правило, контекст документа можно рассматривать как расположение в исходном файле, в то время как контекст кода является позицией инструкции кода в потоке выполнения.

## <a name="see-also"></a>См. также раздел
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
