---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bacf4fffe9c4cf6a3f54bff8a941b5e680cd57cf
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210305"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Этот метод создает службу визуализатора.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>Параметры
`binder`\
[in] [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) объект, передаваемый в [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).

`pSymProv`\
[in] [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) объект, передаваемый в `IDebugParsedExpression::EvaluateSync`.

`pAddress`\
[in] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объект, передаваемый в `IDebugParsedExression::EvaluateSync`.

`dataProvider`\
[in] Объект, реализующий интерфейс [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) интерфейс (указанного в вычислителе выражений).

`ppService`\
[out] Служба создана.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 `binder`, `pSymProv`, И `pAddress` параметры были переданы для `IDebugParsedExpression::EvaluateSync` метод. `CreateVisualizerService` должна быть вызвана только из `IDebugParsedExpression::EvaluateSync` как часть вычислитель выражений поддержка визуализаторами типов.

## <a name="see-also"></a>См. также
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)