---
title: Ошибки точки останова | Документация Майкрософт
description: Сведения о процессе, когда точка останова пытается выполнить привязку к коду, но завершается ошибкой и устранение ошибок точки останова.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88a5003ce8abe79fcba9f9604047d2265810fda2
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914495"
---
# <a name="breakpoint-errors"></a>Ошибки точки останова
Ниже описывается процесс, когда точка останова пытается выполнить привязку к коду, но завершается ошибкой.

## <a name="troubleshoot-a-breakpoint-error"></a>Устранение ошибки точки останова

1. Модуль отладки (DE) отправляет [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) в Диспетчер отладки сеансов (SDM).

2. Модель SDM вызывает [IDebugBreakpointErrorEvent2:: жетеррорбреакпоинт](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP` ) для получения точки останова по ошибке.

3. Модель SDM вызывает [IDebugErrorBreakpoint2:: жетпендингбреакпоинт](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) для получения ожидающей точки останова, из которой поступила точка останова ошибки.

4. Модель SDM вызывает [IDebugErrorBreakpoint2:: жетбреакпоинтресолутион](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) , чтобы получить причину, по которой не удалось выполнить привязку точки останова по ошибке.

## <a name="see-also"></a>См. также раздел
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
