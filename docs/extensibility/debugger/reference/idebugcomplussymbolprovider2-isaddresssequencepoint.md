---
title: IDebugComPlusSymbolProvider2::IsAddressSequencePoint | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::IsAddressSequencePoint
- IsAddressSequencePoint
ms.assetid: 89b27c57-5295-428b-8229-a402500d8cd3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc56d0bda7d8b1797c29db6c2e72a5efc3d586d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62876408"
---
# <a name="idebugcomplussymbolprovider2isaddresssequencepoint"></a>IDebugComPlusSymbolProvider2::IsAddressSequencePoint
Определяет, является ли адрес отладки с указанной точкой следования.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsAddressSequencePoint(
    IDebugAddress* pAddress
);
```

```csharp
int IsAddressSequencePoint(
    IDebugAddress pAddress
);
```

#### <a name="parameters"></a>Параметры
`pAddress`

 [in] Отладка адрес, представленный [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.

## <a name="return-value"></a>Возвращаемое значение
Если адрес отладки является точкой следования, возвращает `S_OK`; в противном случае возвращает `S_FALSE`.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для **CDebugSymbolProvider** объекта, который предоставляет [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) интерфейс.

```cpp
HRESULT CDebugSymbolProvider::IsAddressSequencePoint(
    IDebugAddress* pAddress
)
{
    HRESULT hr = S_OK;
    CDEBUG_ADDRESS address;
    CComPtr<CModule> pModule;

    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );

    IfFalseGo( pAddress, E_INVALIDARG );

    IfFailGo( pAddress->GetAddress( &address ) );

    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );

    IfFailGo( GetModule( address.GetModule(), &pModule) );

    if (!pModule->IsSequencePoint( address.addr.addr.addrMethod.tokMethod,
                                   address.addr.addr.addrMethod.dwVersion,
                                   address.addr.addr.addrMethod.dwOffset ))
    {

        // S_FALSE indicates this is not a sequence point

        hr = S_FALSE;
    }

Error:

    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );

    return hr;
}
```

## <a name="see-also"></a>См. также
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
