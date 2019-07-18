---
title: IEEVisualizerService::GetCustomViewerList | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4fa71a731843f1deed1cfe9a464cc4ab716a8a43
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350173"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Этот метод возвращает список визуализаторов типов, эта служба, о которых известно.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCustomViewerList(
   ULONG                celtSkip,
   ULONG                celtRequested,
   DEBUG_CUSTOM_VIEWER* rgViewers,
   ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
   uint                  celtSkip,
   uint                  celtRequested,
   DEBUG_CUSTOM_VIEWER[] rgViewers,
   out uint              pceltFetched
);
```

## <a name="parameters"></a>Параметры
`celtSkip`\
[in] Число визуализаторы для пропуска.

`celRequested`\
[in] Число визуализаторы для извлечения (также указывает размер `rgViewers` массива).

`rgViewers`\
[in, out] Массив [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) структур для заполнения.

`pceltFetched`\
[out] Число фактически извлеченных визуализаторы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) передает запрос в этот метод как часть поддержки для визуализаторов типов. Если средство оценки выражений также поддерживает пользовательские средства просмотра для одного типа, оно может Дописывать соответствующим образом заполненную [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) структуры для этих пользовательских средств просмотра, в список. Убедитесь, что [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) отражает этих дополнительных средств просмотра.

 См. в разделе [визуализатор типов и пользовательские средства просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Дополнительные сведения о различиях между визуализаторы, а также средства просмотра.

## <a name="see-also"></a>См. также
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)