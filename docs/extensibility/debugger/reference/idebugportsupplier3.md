---
title: IDebugPortSupplier3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d45d8d93f26ef01fb184811a87b4f4fcc4483340
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840240"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Этот интерфейс позволяет вызывающему объекту определить, может ли поставщик порта сохранять порты (путем записи их на диск) между вызовами отладчика, а затем получать список сохраненных портов.

## <a name="syntax"></a>Синтаксис

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Пользовательский поставщик портов реализует этот интерфейс для поддержки сохранения или сохранения сведений о портах на диск. Этот интерфейс должен быть реализован на том же объекте, что и интерфейс [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) .

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызовите [QueryInterface](/cpp/atl/queryinterface) в `IDebugPortSupplier2` интерфейсе, чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 В дополнение к методам, унаследованным от интерфейса [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) , этот интерфейс поддерживает следующие действия:

|Метод|Описание|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Возвращает значение, указывающее, может ли поставщик порта сохранять порты (путем записи на диск) между вызовами отладчика.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Возвращает объект, который можно использовать для перечисления всех портов, записанных на диск этим поставщиком портов.|

## <a name="remarks"></a>Remarks
 Если поставщик порта может сохранять порты между вызовами, он должен реализовать этот интерфейс. Порты должны быть загружены при создании экземпляра поставщика порта и записаны на диск при уничтожении поставщика порта.

 Модуль отладки обычно не взаимодействует с поставщиком порта и не будет использовать его для этого интерфейса.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
