---
title: IDebugComPlusSymbolProvider::GetNameFromToken | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetNameFromToken
- GetNameFromToken
ms.assetid: 6e8cf468-5fd1-4655-93ed-88828d6068b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 778a6f90dcc20ad19e310fb6ddd7680318dc3c98
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336723"
---
# <a name="idebugcomplussymbolprovidergetnamefromtoken"></a>IDebugComPlusSymbolProvider::GetNameFromToken
Возвращает имя, связанное с заданным токеном, заданный его объект метаданных.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetNameFromToken (
    IUnknown* pMetadataImport,
    DWORD     dwToken,
    BSTR*     pbstrName
);
```

```csharp
int GetNameFromToken (
    object     pMetadataImport,
    uint       dwToken,
    out string pbstrName
);
```

## <a name="parameters"></a>Параметры
`pMetadataImport`\
[in] Объект, содержащий сведения о метаданных.

`dwToken`\
[in] Токен имел имя.

`pbstrName`\
[out] Имя, которое соответствует токену.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для **CDebugSymbolProvider** объекта, который предоставляет [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) интерфейс.

```cpp
HRESULT CDebugSymbolProvider::GetNameFromToken(
    IUnknown* pMetadataImport,
    DWORD dwToken,
    BSTR* pbstrName
)
{
    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetaData;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pMetadataImport, IUnknown));

    METHOD_ENTRY(CDebugSymbolProvider::GetNameFromToken);

    IfFalseGo( pMetadataImport && pbstrName, E_INVALIDARG );

    *pbstrName = NULL;
    IfFailGo( pMetadataImport->QueryInterface( IID_IMetaDataImport,
              (void**) &pMetaData ) );

    switch ( TypeFromToken(dwToken) )
    {
        case mdtModule:
            IfFailGo( GetModuleName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtTypeDef:
            IfFailGo( GetTypeName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtFieldDef:
            IfFailGo( GetFieldName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtMethodDef:
            IfFailGo( GetMethodName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtEvent:
            IfFailGo( GetEventName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtProperty:
            IfFailGo( GetPropertyName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtAssembly:
            IfFailGo( GetAssemblyName( pMetaData, dwToken, pbstrName) );
            break;

        default:
            ASSERT(!"Unsupported token passed to GetNameFromToken");
            hr = E_FAIL;
            break;
    }

Error:

    METHOD_EXIT(CDebugSymbolProvider::GetNameFromToken, hr);
    return hr;
}
```

## <a name="see-also"></a>См. также
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
