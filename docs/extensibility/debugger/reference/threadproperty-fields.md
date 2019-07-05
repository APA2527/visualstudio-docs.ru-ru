---
title: THREADPROPERTY_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9da7b995826b905af7faf6cac3fa0fc3d5ceba5e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316207"
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
Указывает, какие сведения о потоке требуется получить.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
typedef DWORD THREADPROPERTY_FIELDS;
```

```csharp
public enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Поля
 `TPF_ID`\
 Инициализация и использование `dwThreadId` поле [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) структуры.

 `TPF_SUSPENDCOUNT`\
 Инициализация и использование `dwSuspendCount` поле `THREADPROPERTIE`структура.

 `TPF_STATE`\
 Инициализация и использование `dwThreadState` поле `THREADPROPERTIE`структура.

 `TPF_PRIORITY`\
 Инициализация и использование `bstrPriority` поле `THREADPROPERTIE`структура.

 `TPF_NAME`\
 Инициализация и использование `bstrName` поле `THREADPROPERTIE`структура.

 `TPF_LOCATION`\
 Инициализация и использование `bstrLocation` поле `THREADPROPERTIE`структура.

 `TPF_ALLFIELDS`\
 Указывает все поля.

## <a name="remarks"></a>Примечания
 Эти значения передаются в качестве аргумента [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) метод, чтобы указать, какие поля [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) структуры должны быть инициализированы.

 Эти значения также используются в `dwFields` членом `THREADPROPERTIES` структура указывает, какие поля используются и допустимым.

 Эти флаги могут быть объединены с побитовым объектом `OR`.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)