---
title: Реализация вычислителя выражений | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66a1a0cb78036982923d20e39a3a4c32b288e459
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326194"
---
# <a name="implement-an-expression-evaluator"></a>Реализация вычислителя выражений
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образец средства оценки выражений управляемый](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Вычисления выражения является сложным взаимодействием между модуль отладки (DE), поставщик символов (SP), объект модуля привязки и средство оценки выражений (EE). Эти четыре компонента соединены с интерфейсами, реализованный в одном компоненте и использованы другим.

 EE принимает выражение из DE в виде строки и анализирует и оценивает его. EE запускает следующие интерфейсы, которые могут использоваться DE:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE вызывает объект связыватель, предоставленный DE, чтобы получить это значение, символы и объектов. EE использует следующие интерфейсы, реализуемые с DE:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  Запускает EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` предоставляет механизм для описания результат вычисления выражения, такие как локальная переменная, примитив или объект для Visual Studio, которая затем отображает соответствующую информацию в **"Локальные"** , **контрольных значений** , или **Интерпретация** окна.

  SP присваивается EE путем DE, когда он запрашивает сведения. Хранимая процедура выполняется интерфейсы, которые описывают адреса и поля, такие как следующие интерфейсы, а также производных:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE использует все эти интерфейсы.

## <a name="in-this-section"></a>Содержание раздела
 [Стратегия реализации вычислителя выражений](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) определяет трехшаговый процесс стратегия реализации вычислителя (EE) выражений.

## <a name="see-also"></a>См. также
- [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)