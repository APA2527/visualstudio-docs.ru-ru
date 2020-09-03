---
title: Реализация средства оценки выражений | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8c7c9a1130794dd4c28f212afd6cb3c030f5a1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738537"
---
# <a name="implement-an-expression-evaluator"></a>Реализация средства оценки выражений
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Вычисление выражения является сложной взаимозависимостьой между модулем отладки (DE), поставщиком символов (SP), объектом BINDER и вычислителем выражений (EE). Эти четыре компонента соединены интерфейсами, которые реализуются одним компонентом и используются другим.

 EE принимает выражение из DE в виде строки и выполняет синтаксический анализ или оценку. EE выполняет следующие интерфейсы, которые используются методом DE:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE вызывает объект связывателя, предоставленный методом DE, для получения значения символов и объектов. EE использует следующие интерфейсы, которые реализуются методом DE:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  EE запускает [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` предоставляет механизм для описания результата вычисления выражения, например локальной переменной, примитива или объекта в Visual Studio, который затем отображает соответствующую информацию в окне " **локальные**", " **Контрольные значения**" или " **Интерпретация** ".

  Пакет обновления передается в EE на DE при запросе информации. SP запускает интерфейсы, описывающие адреса и поля, такие как следующие интерфейсы и их производные:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE потребляет все эти интерфейсы.

## <a name="in-this-section"></a>В этом разделе
 [Стратегия реализации средства оценки выражений](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) Определяет процесс в три этапа для стратегии реализации средства оценки выражений (EE).

## <a name="see-also"></a>См. также раздел
- [Написание вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
