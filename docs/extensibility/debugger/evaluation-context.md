---
title: Контекст оценки | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6a3d74c26b6ca94e0a4052df4810e407313a6cd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315503"
---
# <a name="evaluation-context"></a>Контекст оценки
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образец средства оценки выражений управляемый](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Когда модуль отладки (DE) вызывает средство оценки выражений (EE), три аргумента, передаваемые [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) определить контекст для поиск и пробное использование символов, как показано в следующей таблице.

## <a name="arguments"></a>Аргументы

|Аргумент|Описание|
|--------------|-----------------|
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) интерфейс, который задает обработчик символов (SH) для использования для идентификации символа.|
|`pAddress`|[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) интерфейс, определяющий текущей точки выполнения. Этот интерфейс находит метод, который содержит выполняемый код.|
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) интерфейс, который находит значение и тип символа, заданную ее именем.|

 `IDebugParsedExpression::EvaluateSync` Возвращает [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, представляющий результирующее значение и его тип.

## <a name="see-also"></a>См. также
- [Интерфейсы вычислителя ключевых выражений](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)