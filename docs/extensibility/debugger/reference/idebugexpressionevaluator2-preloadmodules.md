---
title: IDebugExpressionEvaluator2::P Релоадмодулес | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::PreloadModules
- PreloadModules
ms.assetid: bcf9b968-ee14-4a92-88ad-926268a44e03
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6998b847d400c9eb5e999a7299f5bedec0982253
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948300"
---
# <a name="idebugexpressionevaluator2preloadmodules"></a>IDebugExpressionEvaluator2::PreloadModules
Предварительно загружает модули, назначенные указанным поставщиком символов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT PreloadModules (
    IDebugSymbolProvider* pSym
);
```

```csharp
int PreloadModules (
    IDebugSymbolProvider pSym
);
```

## <a name="parameters"></a>Параметры
`pSym`\
окне Поставщик символов, для которого будут предварительно загружены модули.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
Этот необязательный метод используется при выполнении присоединения ведущего процесса. Он дает EE возможность "прогрев" в составе подключения.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для объекта **експрессионевалуаторпаккаже** , предоставляющего интерфейс [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) .

```cpp
STDMETHODIMP ExpressionEvaluatorPackage::PreloadModules
(
    IDebugSymbolProvider *pSym
)
{
    HRESULT hr = NOERROR;
    RuntimeMemberDescriptor  * prtMemberDesc;
    RuntimeClassDescriptor *prtClassDesc;
    CComPtr<IDebugClassField> pClassField;
    IfFalseGo(pSym,E_INVALIDARG);

    prtMemberDesc = &(g_rgRTLangMembers[StandardModuleAttributeCtor]);
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);

    pClassField = NULL;
    prtMemberDesc = &(g_rgRTLangMembers[LoadAssembly]);
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);

Error:
    return hr;
}
```

## <a name="see-also"></a>См. также раздел
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
