---
title: IEnumDebugThreads2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76a7267690f359d960a0c5e9b6f6a1c502d5d4f1
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461182"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Этот интерфейс перечисляет поток, выполняемый в текущий сеанс отладки.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для представления списка потоков в программе.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовите [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) для получения этого интерфейса, представляющий список всех потоков во всех программах, выполняющийся в процессе. Вызовите [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) для получения этого интерфейса, представляющий список потоков, выполняющих в программе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugThreads2`.

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Извлекает указанное число потоков в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Пропускает указанное число потоков в последовательности перечисления.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Получает количество потоков в перечислителе.|

## <a name="remarks"></a>Примечания
 Visual Studio обычно получает этот интерфейс для обновления **потоков** окно также, как получить первый поток списка, чтобы вызвать [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md), и [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
