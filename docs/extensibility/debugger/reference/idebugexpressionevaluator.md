---
title: IDebugExpressionEvaluator | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7606f01d180c0c26ad0e2f82e5d83a7256e3d64
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325623"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Этот интерфейс представляет средство оценки выражений.

## <a name="syntax"></a>Синтаксис

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
Средство оценки выражений должен реализовывать этот интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
Чтобы получить этот интерфейс, следует создать средство оценки выражений через `CoCreateInstance` метод с помощью класса идентификатор CLSID средства вычисления. См. пример.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
В следующей таблице показаны методы `IDebugExpressionEvaluator`.

|Метод|Описание|
|------------|-----------------|
|[Анализ](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Преобразует строку выражения проанализированное выражение.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Возвращает локальные переменные, аргументы и другие свойства для метода.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Преобразует метод расположение и смещение в адрес памяти.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Определяет, какой язык следует использовать для создания печатного результатов.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Задает корневой раздел реестра. Используется для отладки side-by-side.|

## <a name="remarks"></a>Примечания
В типичной ситуации, модуль отладки (DE) создает средство оценки выражений (EE) в результате вызова [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Поскольку DE знает, язык и поставщиком EE, он хочет использовать, DE возвращает CLSID EE из реестра ( [вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) функция, `GetEEMetric`, помогает в этом извлечение).

После создания экземпляра EE DE вызывает [проанализировать](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) синтаксический анализ выражения и сохраните его в [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) объекта. Позже вызов [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) вычисляет выражение.

## <a name="requirements"></a>Требования
Заголовок: ee.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример
В этом примере показано, как создать экземпляр средство оценки выражений, назначить поставщика символов и адрес в исходном коде. В этом примере используется функция `GetEEMetric`, из [вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) библиотеки, dbgmetric.lib.

```cpp
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,
                                                 IDebugAddress *pSourceAddress)
{
    // This is typically defined globally but is specified here just
    // for this example.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";

    IDebugExpressionEvaluator *pEE = NULL;
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {
        HRESULT hr         = S_OK;
        GUID  languageGuid = { 0 };
        GUID  vendorGuid   = { 0 };

        hr = pSymbolProvider->GetLanguage(pSourceAddress,
                                          &languageGuid,
                                          &vendorGuid);
        if (SUCCEEDED(hr)) {
            CLSID clsidEE = { 0 };
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;
            // Get the expression evaluator's CLSID from the registry.
            ::GetEEMetric(languageGuid,
                          vendorGuid,
                          metricCLSID,
                          &clsidEE,
                          strRegistrationRoot);
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {
                // Instantiate the expression evaluator.
                spExpressionEvaluator.CoCreateInstance(clsidEE);
            }
            if (spExpressionEvaluator != NULL) {
                pEE = spExpressionEvaluator.Detach();
            }
        }
    }
    return pEE;
}
```

## <a name="see-also"></a>См. также
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
