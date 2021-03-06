---
title: Контекст оценки | Документация Майкрософт
description: 'Когда модуль отладки вызывает средство оценки выражений, аргументы определяют контекст для поиска и вычисления символов: Псимболпровидер, Паддресс и Пбиндер.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0957a204a83ab72aabe14fe4a70d8e758e83a08f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840591"
---
# <a name="evaluation-context"></a>Контекст оценки
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Когда модуль отладки (DE) вызывает средство оценки выражений (EE), три аргумента, передаваемые в [евалуатесинк](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , определяют контекст для поиска и вычисления символов, как показано в следующей таблице.

## <a name="arguments"></a>Аргументы

|Аргумент|Описание|
|--------------|-----------------|
|`pSymbolProvider`|Интерфейс [идебугсимболпровидер](../../extensibility/debugger/reference/idebugsymbolprovider.md) , указывающий обработчик символов (SH), используемый для обозначения символа.|
|`pAddress`|Интерфейс [идебугаддресс](../../extensibility/debugger/reference/idebugaddress.md) , указывающий текущую точку выполнения. Этот интерфейс находит метод, содержащий выполняемый код.|
|`pBinder`|Интерфейс [идебугбиндер](../../extensibility/debugger/reference/idebugbinder.md) , который находит значение и тип символа по его имени.|

 `IDebugParsedExpression::EvaluateSync` Возвращает интерфейс [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , представляющий результирующее значение и его тип.

## <a name="see-also"></a>См. также раздел
- [Интерфейсы средства оценки ключевых выражений](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
