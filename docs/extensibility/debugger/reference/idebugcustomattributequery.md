---
title: IDebugCustomAttributeQuery | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea9c37dbb889a622d0b428d53144c27d0c04aef9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875975"
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
Представляет запрос для настраиваемых атрибутов для метода или типа.

## <a name="syntax"></a>Синтаксис

```
IDebugCustomAttributeQuery : IUnknown
```

## <a name="methods"></a>Методы
 Этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|Извлекает настраиваемый атрибут с заданным именем.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|Определяет, в указанном определен пользовательский атрибут.|

## <a name="requirements"></a>Требования
 Заголовок: Sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll