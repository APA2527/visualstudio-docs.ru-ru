---
title: m_action поле | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5bd2d826f1612be3bc3747cdaee9818d4ecc870
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925323"
---
# <a name="m_action-field"></a>m_action поле
Делегат, представляющий код для выполнения в <xref:System.Threading.Tasks.Task> объекте.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Так как вы не можете получить доступ к этому внутреннему элементу из платформа .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.

## <a name="syntax"></a>Синтаксис

```csharp
.field assembly object m_action
```

## <a name="remarks"></a>Remarks
 Это `action` параметр в <xref:System.Threading.Tasks.Task.%23ctor%2A> конструкторе.

## <a name="see-also"></a>См. также раздел
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
