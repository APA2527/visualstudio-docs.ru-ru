---
title: OPTNAMECHANGEPFN | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6107f48f4680cef9cbb825f4d760f3f0bac1ec1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336229"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Это функция обратного вызова, указанный в вызове к [SccSetOption](../extensibility/sccsetoption-function.md) (с помощью параметра `SCC_OPT_NAMECHANGEPFN`) и используется для связи имя изменения, внесенные системой управления версиями подключаемого модуля обратно в интегрированной среде разработки.

## <a name="signature"></a>Подпись

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Параметры
 pvCallerData

[in] Значение пользователя, указанное в предыдущем вызове [SccSetOption](../extensibility/sccsetoption-function.md) (с помощью параметра `SCC_OPT_USERDATA`).

 pszOldName

[in] Имя исходного файла.

 pszNewName

[in] Назовите файл был переименован в.

## <a name="return-value"></a>Возвращаемое значение
 Отсутствует.

## <a name="remarks"></a>Примечания
 При переименовании файла во время операции управления версиями, подключаемый модуль системы управления версиями может уведомить об изменении через этот обратный вызов интегрированной среды разработки.

 Если интегрированная среда разработки не поддерживает этот обратный вызов, он не вызывает [SccSetOption](../extensibility/sccsetoption-function.md) указать его. Если подключаемый модуль не поддерживает этот обратный вызов, он будет возвращать `SCC_E_OPNOTSUPPORTED` из `SccSetOption` функционировать при попытке задать обратный вызов интегрированной среды разработки.

## <a name="see-also"></a>См. также
- [Функции обратного вызова, реализованные интегрированной среды разработки](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)