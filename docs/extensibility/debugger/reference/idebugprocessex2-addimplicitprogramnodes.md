---
title: 'IDebugProcessEx2:: АддимплиЦитпрограмнодес | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ef9379edc9e02e8bed6761abf0aa4a2830fc415
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861092"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Этот метод добавляет узел программы для каждого указанного модуля отладки (DE).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT AddImplicitProgramNodes(
   REFGUID guidLaunchingEngine,
   GUID*   rgguidSpecificEngines,
   DWORD   celtSpecificEngines
);
```

```csharp
int AddImplicitProgramNodes(
   ref Guid guidLaunchingEngine,
   Guid[]   rgguidSpecificEngines,
   uint     celtSpecificEngines
);
```

## <a name="parameters"></a>Параметры
`guidLaunchingEngine`\
окне Параметр `GUID` de, который используется для запуска программ (предполагает добавление собственных узлов программы).

`rgguidSpecificEngines`\
окне Массив типа `GUID` DEs, для которого будут добавлены узлы программ.

`celtSpecificEngines`\
окне Число элементов `GUID` в `rgguidSpecificEngines` массиве.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
- [Узлы программы](../../../extensibility/debugger/program-nodes.md) будут добавляться для каждого из них, кроме `rgguidSpecificEngines` модуля запуска (как указано в `guidLaunchingEngine` ), который предполагает добавление собственного узла программы при запуске программы.

## <a name="see-also"></a>См. также раздел
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Узлы программы](../../../extensibility/debugger/program-nodes.md)
