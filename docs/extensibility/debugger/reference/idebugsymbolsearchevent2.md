---
title: IDebugSymbolSearchEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ad5fa763be8929a9122a6fd7517b401f5a874e04
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909344"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Этот интерфейс отправляется модулем отладки (DE) для указания того, что отладочные символы для отлаживаемого модуля были загружены.

## <a name="syntax"></a>Синтаксис

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Метод DE реализует этот интерфейс для сообщения о том, что символы модуля загружены. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. Модель SDM использует [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейсу.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Параметр DE создает и отправляет этот объект события для сообщения о том, что символы модуля загружены. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , предоставляемой SDM при присоединении к отлаживаемой программе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 `IDebugSymbolSearchEvent2`Интерфейс предоставляет следующий метод.

|Метод|Описание|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Извлекает сведения о результатах поиска символов.|

## <a name="remarks"></a>Remarks
 Это событие будет отправлено, даже если не удалось загрузить символы. Вызов `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` позволяет обработчику этого события определить, действительно ли в модуле имеются символы.

 Visual Studio обычно использует это событие для обновления состояния загруженных символов в окне **модули** .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
