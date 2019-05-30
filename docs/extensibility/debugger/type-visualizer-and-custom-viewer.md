---
title: Тип визуализатора и пользовательское средство просмотра | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01f058f959c9af78e196112cc49b63d293e8e31d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341267"
---
# <a name="type-visualizer-and-custom-viewer"></a>Визуализатор типов и пользовательское средство просмотра
Тип визуализатора — это компонент, который отображает часть данных в определенном формате. Формат — полностью до кто реализует визуализатор, будь то, как конечный пользователь или стороннего поставщика визуализаторов.

 Пользовательское средство просмотра является частью вычислитель пользовательского выражения, который отображает часть данных в определенном формате. Этот формат полностью определяется разработчиком пользовательского средства просмотра, это означает, что форматом отводится зависит от разработчика вычислитель выражений (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Поддержка визуализаторами типа вычислитель выражений
 EE поддерживает визуализаторов типов, поддерживая набор интерфейсов, доступных для визуализаторов: интерфейсы, такие как [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) и [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Тем не менее, EE не отвечает за реализацию визуализатор типов, сам: EE просто позволяет визуализаторы внешний доступ к информации о его типе. Такие визуализаторы может быть отправлена вместе с EE и установлены в нужном месте в Visual Studio, предоставленные другой сторонних поставщиков и даже конечный пользователь.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Поддержка пользовательских средств просмотра в вычислитель выражений
 EE также поддерживает пользовательские средства просмотра, в которых EE, сам предоставляет код для просмотра типа данных. Реализует пользовательское средство просмотра [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) требуется интерфейс, который обрабатывает все операции отображения данных в предпочитаемом формате; средство просмотра имеет полный контроль над отображение и можно даже позволить изменять данные. Любые пользовательские средства просмотра, предоставляемые EE снабжены EE после выпуска продукта.

## <a name="see-also"></a>См. также
- [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)
- [Вычислитель выражений](../../extensibility/debugger/expression-evaluator.md)
- [Отладка ядра](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)