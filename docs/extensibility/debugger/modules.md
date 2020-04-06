---
title: Модули Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abdf76c7f5f031d2ef7f3bcac2bae8a2c508b783
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738349"
---
# <a name="modules"></a>Модули
С точки зрения архитектуры отладчика *модуль:*

- Является физическим контейнером кода, например, исполняемым файлом или DLL.

- Можно перезагрузить его символы и описать себя. Описания модулей отображаются в окне модулей IDE.

- Представлен интерфейсом [IDebugModule2,](../../extensibility/debugger/reference/idebugmodule2.md) созданным движком отладки для описания модуля.

## <a name="see-also"></a>См. также
- [Концепции debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
