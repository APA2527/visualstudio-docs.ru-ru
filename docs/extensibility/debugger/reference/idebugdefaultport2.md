---
title: IDebugDefaultPort2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fca0b999f4c5878debbdee556431d56b7977c719
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901853"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Этот интерфейс предоставляет несколько методов для доступа к серверу и средствам уведомления на порту.

## <a name="syntax"></a>Синтаксис

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Visual Studio реализует этот интерфейс, чтобы представить порт отладки для доступа к программам. Пользовательский поставщик порта также может реализовать этот интерфейс, если он обрабатывает удаленную отладку.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс предоставляет аргумент для методов в интерфейсе [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) . Вызов [QueryInterface](/cpp/atl/queryinterface) в интерфейсе [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) также может получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 В дополнение к методам, определенным в [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Получает интерфейс уведомления порта от этого порта.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Возвращает интерфейс для сервера, на котором размещен этот порт.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Определяет, работает ли этот порт на локальном компьютере.|

## <a name="remarks"></a>Remarks
 Имя " `IDebugDefaultPort2` " является битом атрибутаDurableService, так как оно не представляет порт по умолчанию. Его можно назвать «IDebugPort3».

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
