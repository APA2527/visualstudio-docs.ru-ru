---
title: IDebugField | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a036f6d08c6f88a30f8a8c9ab6d0d2e847065854
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62873929"
---
# <a name="idebugfield"></a>IDebugField
Этот интерфейс представляет поле, то есть описание символа или тип.

## <a name="syntax"></a>Синтаксис

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Символ поставщик реализует этот интерфейс как базовый класс для всех полей.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Этот интерфейс является базовым классом для всех полей. На основе возвращаемого значения из [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), этот интерфейс может возвращать более специализированных интерфейсов с помощью [QueryInterface](/cpp/atl/queryinterface). Кроме того, многие интерфейсы возвращают `IDebugField` объекты из различных методов.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugField`.

|Метод|Описание|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Получает отображаемую информацию о символ или типа.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Возвращает тип поля.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Возвращает тип поля.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Возвращает контейнер поля.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Возвращает адрес поля.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Получает размер поля в байтах.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Возвращает расширенные сведения о поле.|
|[Equal](../../../extensibility/debugger/reference/idebugfield-equal.md)|Сравнивает два поля.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Получает сведения зависят от типов символов или типа.|

## <a name="remarks"></a>Примечания
 Язык C эквивалентен типу `typedef`.

 В следующем примере язык C++ `weather` является типом класса и `sunny` и `stormy` представляют собой символы:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Поле представляет символ ли тип можно определить путем вызова [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) и изучив [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) результат. Если `FIELD_KIND_TYPE` установлен бит, поле имеет тип и если `FIELD_KIND_SYMBOL` бит устанавливается, он является символьным.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)