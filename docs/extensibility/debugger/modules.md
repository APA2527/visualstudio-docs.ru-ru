---
title: Модули | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 611d067030cd935f6957a976c8a3aa2b7d4f8ae3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925406"
---
# <a name="modules"></a>Модули
С точки зрения архитектуры отладчика *модуль*:

- — Это физический контейнер кода, например исполняемый файл или библиотеку DLL.

- Можно перезагрузить его символы и описать сам себя. Описание модуля, отображаются в интегрированной среды разработки окна "Модули".

- Представленный [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) интерфейса, созданные модуля отладки для описания модуля.

## <a name="see-also"></a>См. также
- [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)