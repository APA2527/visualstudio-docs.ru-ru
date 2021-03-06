---
title: Перечислитель кода состояния каталога | Документация Майкрософт
description: Перечислитель Сккдирстатус содержит именованные постоянные значения, указывающие состояние каталога в системе управления версиями и используемое Сккдиркуеринфо.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af72b9e14695cb954084abebc3a3c336c90af73d
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996127"
---
# <a name="directory-status-code-enumerator"></a>Перечислитель кода состояния каталога
`SccDirStatus`Перечислитель содержит именованные постоянные значения, указывающие состояние каталога в системе управления версиями. Это перечисление используется [сккдиркуеринфо](../extensibility/sccdirqueryinfo-function.md). Это было представлено в версии 1,2 API подключаемого модуля системы управления версиями.

## <a name="syntax"></a>Синтаксис

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Члены
 Не удалось получить состояние SCC_DIRSTATUS_INVALID; не полагайтесь на нее.

 SCC_DIRSTATUS_NOTCONTROLLED каталог не находится в системе управления версиями.

 SCC_DIRSTATUS_CONTROLLED Directory находится в системе управления версиями.

 Проект SCC_DIRSTATUS_EMPTYPROJ, соответствующий этому каталогу, пуст.

## <a name="see-also"></a>См. также раздел
- [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
