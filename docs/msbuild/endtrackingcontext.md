---
title: EndTrackingContext | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf982200b8e65e404325bdbd189ff3b0f2daebac
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634244"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

Конц текущего контекста отслеживания.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Возвращаемое значение

**HRESULT** с установленным битом **SUCCEEDED**, если контекст отслеживания был закончен.

## <a name="requirements"></a>Требования

**Заголовок.** *FileTracker.h*

## <a name="see-also"></a>См. также

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
