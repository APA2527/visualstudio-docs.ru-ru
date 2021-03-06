---
title: Вычисление выражений в режиме приостановки выполнения | Документация Майкрософт
description: Сведения о процессе, который происходит, когда отладчик находится в режиме приостановки выполнения и должен выполнять оценку выражений.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 041e499f4c670b5b31530c7fc0ecb74358a8087f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921497"
---
# <a name="expression-evaluation-in-break-mode"></a>Вычисление выражений в режиме приостановки выполнения
В следующем разделе описывается процесс, выполняемый, когда отладчик находится в режиме приостановки выполнения и должен выполняться вычисление выражения.

## <a name="expression-evaluation-process"></a>Процесс оценки выражений
 Ниже приведены основные шаги, используемые при вычислении выражения.

1. Диспетчер отладки сеансов (SDM) вызывает [IDebugStackFrame2:: жетекспрессионконтекст](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения интерфейса контекста выражения [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. Затем SDM вызывает [IDebugExpressionContext2::P арсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) со строкой, которую необходимо проанализировать.

3. Если Парсетекст не возвращает S_OK, то возвращается причина ошибки.

     ином

     Если Парсетекст возвращает S_OK, то модель SDM может затем вызвать либо [IDebugExpression2:: евалуатесинк](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) , либо [IDebugExpression2:: евалуатеасинк](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , чтобы получить конечное значение из проанализированного выражения.

    - При использовании `IDebugExpression2::EvaluateSync` данный интерфейс обратного вызова сообщает о текущем процессе вычисления. Окончательное значение возвращается в интерфейсе [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .

    - При использовании `IDebugExpression2::EvaluateAsync` данный интерфейс обратного вызова сообщает о текущем процессе вычисления. После завершения оценки Евалуатеасинк отправляет интерфейс [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) через обратный вызов. При использовании этого интерфейса событий итоговое значение выдается с помощью параметра [result](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>См. также раздел
- [События отладчика Call](../../extensibility/debugger/calling-debugger-events.md)
