---
title: Модули | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b231ee1eb84f41115a0892cda42a8b7e781e5e53
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350680"
---
# <a name="modules"></a>Модули
С точки зрения архитектуры отладчика *модуль*:

- — Это физический контейнер кода, например исполняемый файл или библиотеку DLL.

- Можно перезагрузить его символы и описать сам себя. Описание модуля, отображаются в интегрированной среды разработки окна "Модули".

- Представленный [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) интерфейса, созданные модуля отладки для описания модуля.

## <a name="see-also"></a>См. также
- [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)