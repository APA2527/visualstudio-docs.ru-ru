---
title: IDebugFunctionPosition2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e05cc09d2c252ddeaadc3cfa1b40e1a5797b6d79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920901"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Этот интерфейс представляет абстрактное расположение функции в исходном документе.

## <a name="syntax"></a>Синтаксис

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс, чтобы представить расположение функции в исходном документе.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс предоставляется как часть объединения [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) (в частности, структуры [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) ), которая в свою очередь является частью структуры [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , используемой при создании ожидающей точки останова.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugFunctionPosition2` .

|Метод|Описание|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Возвращает имя функции, относительно которой находится эта координата.|
|[Пересмещение](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Возвращает смещение от начала функции.|

## <a name="remarks"></a>Remarks
 Расположение, представленное этим интерфейсом, основано на тексте, а именно [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) структуре.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
