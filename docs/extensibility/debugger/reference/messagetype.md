---
title: MESSAGETYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c17860bb47f493031e6db1134aec498611b07f1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339195"
---
# <a name="messagetype"></a>MESSAGETYPE
Указывает тип сообщения и причины.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
typedef DWORD MESSAGETYPE;
```

```csharp
public enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
```

## <a name="fields"></a>Поля
 `MT_OUTPUTSTRING`\
 Указывает, что сообщения должны отправляться в окне вывода. Это взаимно исключают друг друга из `MT_MESSAGEBOX`.

 `MT_MESSAGEBOX`\
 Указывает, что сообщения должны быть видны в окне сообщения. Это взаимно исключают друг друга из `MT_OUTPUTSTRING`.

 `MT_TYPE_MASK`\
 Значение маски для изоляции назначения для сообщения.

 `MT_REASON_EXCEPTION`\
 Указывает, что окно сообщения отображается в результате исключения. Это взаимно исключают друг друга из `MT_REASON_TRACEPOINT`.

 `MT_REASON_TRACEPOINT`\
 Указывает, что в результате обращения к точке трассировки отображается окно сообщения. Это взаимно исключают друг друга для `MT_REASON_EXCEPTION`.

 `MT_REASON_MASK`\
 Значение маски для изоляции причина для отображаемого сообщения.

## <a name="remarks"></a>Примечания
 Эти значения возвращаются из [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) и [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) методы.

 Одно из значений причина могут сочетаться с одним из значений назначения выходных данных при помощи побитовой `OR`.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)