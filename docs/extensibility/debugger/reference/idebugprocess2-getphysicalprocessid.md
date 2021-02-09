---
title: 'IDebugProcess2:: Жетфисикалпроцессид | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetPhysicalProcessId
helpviewer_keywords:
- IDebugProcess2::GetPhysicalProcessId
ms.assetid: 77da6e10-75af-4308-97dd-c44416ca52d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2513278c03c2ec2efed14028a78ab1b1b8ce2f63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890166"
---
# <a name="idebugprocess2getphysicalprocessid"></a>IDebugProcess2::GetPhysicalProcessId
Возвращает идентификатор системного процесса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPhysicalProcessId(
   AD_PROCESS_ID* pdwProcessId
);
```

```csharp
int GetPhysicalProcessId(
   AD_PROCESS_ID[] pdwProcessId
);
```

## <a name="parameters"></a>Параметры
`pdwProcessId`\
заполняет Структура [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) , которая заполняется сведениями об идентификаторе системного процесса.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
