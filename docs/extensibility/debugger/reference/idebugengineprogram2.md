---
title: IDebugEngineProgram2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e5ccf2327e660a983bcb3032363a92ac8a6f71d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730296"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Этот интерфейс обеспечивает поддержку многопоточной отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Обработчик отладки реализует этот интерфейс для поддержки одновременной отладки нескольких потоков. Этот интерфейс реализуется на том же объекте, который реализует интерфейс [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Используйте [QueryInterface](/cpp/atl/queryinterface) для получения этого интерфейса из `IDebugProgram2` интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugEngineProgram2` .

|Метод|Описание|
|------------|-----------------|
|[Остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Останавливает все потоки, выполняющиеся в этой программе.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Отслеживает выполнение (или останавливает наблюдение за выполнением) в заданном потоке.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Разрешает (или запрещает) вычисление выражения в заданном потоке, даже если программа остановлена.|

## <a name="remarks"></a>Remarks
 Visual Studio вызывает этот интерфейс в ответ на событие [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) и устанавливает состояния программы "отслеживать шаг потока" и "отслеживать оценку выражений в потоке". Метод [остановки](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) вызывается всякий раз, когда программа должна быть остановлена. Этот метод дает программе возможность завершить все потоки.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
