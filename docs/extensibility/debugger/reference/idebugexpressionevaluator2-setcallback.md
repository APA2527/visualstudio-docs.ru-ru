---
title: IDebugExpressionEvaluator2::SetCallback | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f347b687066578d5572a89a6e057fd2cb3b79e0b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325488"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Включает средство оценки выражений (EE) для указания интерфейс обратного вызова, отладчик ядра (DE) будет использовать для чтения настроек метрик.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetCallback (
    IDebugSettingsCallback2* pCallback
);
```

```csharp
int SetCallback (
    IDebugSettingsCallback2 pCallback
);
```

## <a name="parameters"></a>Параметры
`pCallback`\
[in] Интерфейс для использования для параметров обратного вызова.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
Этот метод предоставляет интерфейс диспетчеру сеанса отладки, вычислитель выражений можно использовать для чтения настроек метрик. Это полезно в удаленной отладки считывать метрики на [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] компьютера.

## <a name="example"></a>Пример
Ниже показано, как реализовать этот метод для **CEE** объекта, который предоставляет [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) интерфейс.

```cpp
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)
{
    // precondition
    INVARIANT( this );

    // function body
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)
    {
        EEDomain::fSetCallback DomainVal =
        {
            in_pCallback
        };

        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);
        ENSURE( bSuccess );
    }

    // postcondition
    INVARIANT( this );

    return S_OK;
}
```

## <a name="see-also"></a>См. также
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
