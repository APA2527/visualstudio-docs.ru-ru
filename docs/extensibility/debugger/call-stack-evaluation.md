---
title: Вычисление стека вызовов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5557d7eae0ffe54b0f01f1f9e95935d71455229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739174"
---
# <a name="call-stack-evaluation"></a>Оценка стека вызовов
Чтобы просмотреть кадры стека стека вызовов в режиме приостановки выполнения, необходимо реализовать метод [енумфрамеинфо](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .

## <a name="methods-for-evaluation"></a>Методы для оценки
 Для простого модуля отладки (DE) может существовать только один кадр стека. Чтобы изучить кадр стека в режиме приостановки выполнения, необходимо реализовать следующие методы [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).

|Метод|Описание|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Возвращает контекст кода для кадра стека. Контекст кода представляет текущий указатель инструкции в кадре стека.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Возвращает контекст документа для кадра стека. Контекст документа представляет текущее расположение в исходном коде для кадра стека. Требуется для просмотра исходного кода при остановке в программе.|

 Для этих методов требуется реализация нескольких интерфейсов и методов, связанных с контекстом. Поэтому необходимо реализовать метод [жетдокументконтекст](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) и следующие методы [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).

|Метод|Описание|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Возвращает диапазон инструкций File в контексте документа.|

 Чтобы перечислить контексты кода, необходимо реализовать все методы [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).

## <a name="see-also"></a>См. также раздел
- [Контроль выполнения и оценка состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)
