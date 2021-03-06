---
title: IDebugProgramHost2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d0680e0a174716dc79a9819386901d8687422906
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898772"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
Этот интерфейс предоставляет сведения о приложении (процессе).

## <a name="syntax"></a>Синтаксис

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Обработчик отладки реализует этот интерфейс для того же объекта, что и интерфейс [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , чтобы предоставить сведения о ведущем процессе. Это необязательный интерфейс.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызовите [QueryInterface](/cpp/atl/queryinterface) для `IDebugProgram2` интерфейса, чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProgramHost2` .

|Метод|Описание|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Возвращает заголовок, понятное имя или имя файла ведущего процесса этой программы.|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Возвращает идентификатор процесса размещения программы.|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Возвращает имя компьютера, на котором выполняется хост-процесс этой программы.|

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
