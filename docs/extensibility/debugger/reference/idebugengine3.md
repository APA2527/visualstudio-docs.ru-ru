---
title: IDebugEngine3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01f15e088635af30bd36919e3da46dee8b8c237b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352447"
---
# <a name="idebugengine3"></a>IDebugEngine3
Представляет механизм единый отладки (DE), который управляет отладка одного или нескольких модулей.

## <a name="syntax"></a>Синтаксис

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется пользовательский DE (если он поддерживает символы) Включение JustMyCode состояния. Этот интерфейс должен быть реализован DE, если он поддерживает символы и JustMyCode.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Этот интерфейс называется диспетчером сеанса отладки (SDM) для передачи параметров с пользователем для расположения, из которого требуется загрузить символы. Она также называется присвоить идентификатор GUID модуля при создании его экземпляра (этот идентификатор GUID на основе метрик с момента регистрации обработчика). SDM также вызывает этот интерфейс для задания состояния JustMyCode и задать все исключения, известные в отладчике в определенное состояние.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Помимо методов, наследуемых от [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), `IDebugEngine3` интерфейс предоставляет следующие методы.

|Метод|Описание|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Задает путь или пути, DE, используемых для поиска для символов отладки.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Загружает символы для всех модулей, которые еще не были загружены символы, их.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|DE сообщает о JustMyCode.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Задает идентификатор GUID DE на основе метрик.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Задайте необработанный все исключения в определенное состояние.|

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)