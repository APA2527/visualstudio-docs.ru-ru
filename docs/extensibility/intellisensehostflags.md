---
title: IntelliSenseHostFlags | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 882410d68c671a83b13bd14026e5bea4c31cb37e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861640"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Указывает флаги узла IntelliSense.

## <a name="syntax"></a>Синтаксис

```cpp
enum IntellisenseHostFlags
{
    IHF_READONLYCONTEXT      = 0x00000001
    IHF_NOSEPARATESUBJECT    = 0x00000002
    IHF_SINGLELINESUBJECT    = 0x00000004
    IHF_FORCECOMMITTOCONTEXT = 0x00000008
    IHF_OVERTYPE             = 0x00000010
};
```

### <a name="parameters"></a>Параметры

|Участники|Описание|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|Контекстный буфер доступен только для чтения.|
|`IHF_NOSEPARATESUBJECT`|Нет текста темы. Буфер контекста содержит целевой объект IntelliSense (подразумевает `!IHF_READONLYCONTEXT`).|
|`IHF_SINGLELINESUBJECT`|Текст темы не многопроцессорного-строки с поддержкой.|
|`IHF_FORCECOMMITTOCONTEXT`|Эквивалентно `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|Изменения (в предмета или контекста) должны выполняться в режиме замены.|

## <a name="requirements"></a>Требования
 SingleFileeditor.idl

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.TextManager.Interop>