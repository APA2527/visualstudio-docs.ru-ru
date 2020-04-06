---
title: IDebugProperty3::GetStringCharДлин (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringCharLength
helpviewer_keywords:
- IDebugProperty3::GetStringCharLength
ms.assetid: 89a8676b-6da9-4358-91c2-039bf33f99e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c1a2eb62ab748562acd8f0a894a3675f79981ccc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721126"
---
# <a name="idebugproperty3getstringcharlength"></a>IDebugProperty3::GetStringCharLength
Возвращает количество символов в строке связанного свойства.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetStringCharLength(
    ULONG *pLen
);
```

```csharp
int GetStringCharLength(
    out uint pLen
);
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------------|-----------------|
|`pLen`|(ваут) Возвращает количество символов в строке свойства.|

## <a name="return-value"></a>Возвращаемое значение
В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
Как правило, этот метод используется в качестве прелюдии к выделению буфера для вызова методу [GetStringChars.](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для объекта **CProperty,** который предоставляет интерфейс [IDebugProperty3.](../../../extensibility/debugger/reference/idebugproperty3.md)

```cpp
STDMETHODIMP CProperty::GetStringCharLength(ULONG *pLen)
{
    HRESULT hr = E_INVALIDARG;

    EVALFLAGS oldEVALFLAGS = m_EVALFLAGS;

    m_EVALFLAGS &= ~EVAL_NOFUNCEVAL;

    if (pLen)
    {
        DEBUG_PROPERTY_INFO dpInfo;
        dpInfo.bstrValue = NULL;
        ULONG ulen = 0;
        hr = GetPropertyInfo(DEBUGPROP_INFO_VALUE,10,DEFAULT_TIMEOUT,NULL,0,&dpInfo);
        if (hr == S_OK && dpInfo.bstrValue)
        {
            if (wcscmp(dpInfo.bstrValue,L"Nothing") == 0)
            {
                ulen = 0; //VSWhidbey#64815
            }
            else
            {
                ulen = ::SysStringLen(dpInfo.bstrValue);
                if( ulen > 2 &&
                    dpInfo.bstrValue[0] == L'"' &&
                    dpInfo.bstrValue[ulen-1] == L'"')
                {
                    ulen = ulen > 2 ? ulen - 2 : ulen; //remove two double quotes
                }
            }
        }
        ::SysFreeString(dpInfo.bstrValue);
        *pLen = ulen;
    }
    m_EVALFLAGS = oldEVALFLAGS;
    return hr;
}
```

## <a name="see-also"></a>См. также
- [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
