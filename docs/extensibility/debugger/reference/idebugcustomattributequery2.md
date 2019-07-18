---
title: IDebugCustomAttributeQuery2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00220574ac9c16bdab9abd64adde1877ee0fd9f2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335806"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Определяет наличие настраиваемого атрибута для этого поля и, если он существует, возвращает сведения об атрибутах.

## <a name="syntax"></a>Синтаксис

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Символ поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) для поддержки настраиваемых атрибутов.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Используйте [QueryInterface](/cpp/atl/queryinterface) для получения этого интерфейса из [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы **IDebugCustomAttributeQuery** интерфейс.

|Метод|Описание|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Определяет, существует ли настраиваемый атрибут по имени.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Возвращает сведения об атрибутах, для заданного настраиваемого атрибута.|

 В дополнение к **IDebugCustomAttributeQuery** методы, `IDebugCustomAttributeQuery2` реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Возвращает перечислитель для все настраиваемые атрибуты, вложенные в это поле.|

## <a name="remarks"></a>Примечания
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) метод может возвращать перечислитель для всех настраиваемых атрибутов, определенные для данного поля.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)