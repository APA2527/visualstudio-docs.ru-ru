---
title: TASK_STATE_CANCELED поле | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 76de853cfa1fbd524c87384da38a9438c6ac66bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883575"
---
# <a name="task_state_canceled-field"></a>TASK_STATE_CANCELED поле
Задача была отменена до достижения состояния выполнения или подтверждения ее отмены и завершения без исключения.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в mscorlib.dll)

 Так как вы не можете получить доступ к этому внутреннему элементу из платформа .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.

## <a name="syntax"></a>Синтаксис

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Remarks
 Если поле [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) содержит это значение, <xref:System.Threading.Tasks.Task.Status%2A> свойство возвращает <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>См. также раздел
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
