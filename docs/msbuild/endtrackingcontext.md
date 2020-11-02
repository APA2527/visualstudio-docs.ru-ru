---
title: EndTrackingContext | Документы Майкрософт
description: Сведения о синтаксисе, возвращаемом значении и требованиях для использования задачи EndTrackingContext MSBuild для завершения текущего контекста отслеживания.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: da1ef921106732a7787f68a979bc88f3ac012b6d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436673"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

Конц текущего контекста отслеживания.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Возвращаемое значение

**HRESULT** с установленным битом **SUCCEEDED** , если контекст отслеживания был закончен.

## <a name="requirements"></a>Требования

**Заголовок:** *FileTracker.h*

## <a name="see-also"></a>См. также статью

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
