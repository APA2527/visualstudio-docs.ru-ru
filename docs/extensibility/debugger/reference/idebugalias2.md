---
title: IDebugAlias2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00e13da257c5477b3834ebb85bf6d481fe699362
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736365"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Представляет числовой псевдоним для переменной и позволяет средству оценки выражений (EE) получить домен приложения для псевдонима.

## <a name="syntax"></a>Синтаксис

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется управляемым модулем отладки (DE).

## <a name="methods"></a>Методы
 В дополнение к методам в интерфейсе [идебугалиас](../../../extensibility/debugger/reference/idebugalias.md) этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Возвращает идентификатор для домена приложения.|

## <a name="remarks"></a>Remarks
 Псевдоним представляет собой десятичное число в виде строки, за которым следует символ #, например, 1001 #.

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
