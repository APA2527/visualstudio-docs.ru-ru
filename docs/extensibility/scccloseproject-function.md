---
title: Функция Сккклосепрожект | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a4a54193b23015135b6112655fe48d79d3de74e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943157"
---
# <a name="scccloseproject-function"></a>Функция Сккклосепрожект
Эта функция закрывает проект, помечая конец конкретного сеанса.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Параметры
 Пвконтекст структуру контекста подключаемого модуля системы управления версиями.

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Проект успешно закрыт.|
|SCC_E_PROJNOTOPEN|В настоящий момент нет открытых проектов.|
|SCC_E_NOTAUTHORIZED|Пользователю не разрешено выполнять эту операцию.|
|SCC_E_NONSPECIFICERROR|Неконкретный сбой.|

## <a name="remarks"></a>Remarks
 [Сккопенпрожект](../extensibility/sccopenproject-function.md) всегда вызывается перед этой функцией. После вызова этой функции следует вызов `SccOpenProject` функции или [сккунинитиализе](../extensibility/sccuninitialize-function.md), который полностью завершает подключение к системе управления версиями.

## <a name="see-also"></a>См. также раздел
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
