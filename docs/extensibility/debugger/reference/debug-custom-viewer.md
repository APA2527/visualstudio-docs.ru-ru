---
title: DEBUG_CUSTOM_VIEWER | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6fa8e8d9e07510a10b1b32534f3323dab4c84a22
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899101"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Структура, идентифицирующая пользовательское средство просмотра или визуализатор типов.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Члены
`dwID`\
Идентификатор для различения нескольких средств просмотра или визуализаторов, реализованных одним из них `GUID` .

`bstrMenuName`\
Текст, который будет отображаться в раскрывающемся меню.

`bstrDescription`\
Описание пользовательского средства просмотра или визуализатора типов (если оно не используется, должно быть задано значение null).

`guidLang`\
Язык вычислителя выражений.

`guidVendor`\
Поставщик средства оценки выражений.

`bstrMetric`\
Метрика, в которой хранится пользовательское средство просмотра или визуализатор типов `CLSID` .

## <a name="remarks"></a>Remarks
Список этой структуры возвращается путем вызова метода [жеткустомвиеверлист](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) (и, по расширению, метода [жеткустомвиеверлист](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) ).

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
