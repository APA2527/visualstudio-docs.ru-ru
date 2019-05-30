---
title: GETNAME_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1bdcbc4171c8a481ee0c45456ef5600f5150c6d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317586"
---
# <a name="getnametype"></a>GETNAME_TYPE
Задает имя тип файлов для извлечения.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
typedef DWORD GETNAME_TYPE;
```

```csharp
public enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
```

## <a name="fields"></a>Поля
`GN_NAME`\
Указывает понятное имя документа или контекста.

`GN_FILENAME`\
Указывает полный путь документа или контекста.

`GN_BASENAME`\
Указывает имя базового файла, а не полный путь документа или контекста.

`GN_MONIKERNAME`\
Указывает уникальное имя документа или контекста в виде моникер.

`GN_URL`\
Задает имя URL-адрес документа или контекста.

`GN_TITLE`\
Указывает заголовок документа, если он существует.

`GN_STARTPAGEURL`\
Получает URL-адрес начальной страницы для процессов.

## <a name="remarks"></a>Примечания
Эти значения передаются как параметры для [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), и [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) методы, чтобы указать, какие имени для возврата.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
