---
title: IDebugEngineLaunch2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b6f59c9444b0c54f8a230f8eb4487e16b65ebf4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345228"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Используется модулем отладки (DE) для запуска и завершения программы.

## <a name="syntax"></a>Синтаксис

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется пользовательский DE при наличии особых требований для запуска процесса, который не может быть обработан полностью пользовательский порт. Это обычно происходит, когда DE является частью интерпретатор и отлаживаемого процесса — это сценарий: интерпретатор должен запускаться сначала, а затем скрипт загружается и запускается. Порт можно запустить интерпретатор, но скрипт может потребоваться специальная обработка (который является, где DE имеет роль). Этот интерфейс реализуется только в том случае, если есть уникальные требования для запуска программы, которая не может обрабатывать пользовательский порт.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Этот интерфейс называется диспетчером сеанса отладки (SDM) Если этот интерфейс можно получить SDM из [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (с помощью QueryInterface). Если этот интерфейс может быть получен, SDM знает, что DE имеет особые требования и вызывает этот интерфейс, чтобы запустить программу вместо запуска его порт.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugEngineLaunch2`.

|Метод|Описание|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Запускает процесс с помощью DE.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Возобновление выполнения процесса.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Определяет, может быть завершен процесс.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Завершает процесс.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)