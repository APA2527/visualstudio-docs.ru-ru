---
title: 'IDebugProgram3:: Ексекутеонсреад | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8df69c02fb7e78dbb107db906de59d8b7e5881b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887072"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Выполняет программу отладчика. Поток возвращается, чтобы предоставить сведения отладчика о том, какой поток пользователь просматривает при выполнении программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Параметры
`pThread`\
окне Объект [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Существует три разных способа, которые отладчик может возобновить выполнение после остановки.

- EXECUTE: отмена любого предыдущего шага и выполнение до следующей точки останова и т. д.

- Шаг: отмена любого старого шага и выполнение до завершения нового шага.

- Продолжить: выполнить снова и оставить все старое действие активным.

  Поток, передаваемый в, `ExecuteOnThread` полезен при принятии решения о том, какой шаг отменить. Если поток незнаком, выполнение команды EXECUTE отменяет все шаги. Зная о потоке, вам нужно только отменить шаг в активном потоке.

## <a name="see-also"></a>См. также раздел
- [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
