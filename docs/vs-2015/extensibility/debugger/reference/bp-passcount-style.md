---
title: BP_PASSCOUNT_STYLE | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: deb4ce7c464e8518faff55957e1873ef1cd92c39
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153373"
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Задает условие, связанное с числом pass точки останова, которая приводит к срабатыванию точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```csharp  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## <a name="members"></a>Участники  
 BP_PASSCOUNT_NONE  
 Указывает стиль счетчика pass не точки останова.  
  
 BP_PASSCOUNT_EQUAL  
 Задает стиль счетчика pass точки останова равными. Точка останова срабатывает, когда число раз, когда достигается точка останова равно счетчик pass.  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 Устанавливает стиль счетчика pass точку останова равно или больше. Точка останова срабатывает, если количество раз, когда достигается точка останова, равно или больше, чем число pass.  
  
 BP_PASSCOUNT_MOD  
 Указывает число проходов остаток от деления. Например, если количество pass типа `BP_PASSCOUNT_MOD` и передайте значение счетчика равно 4, точка останова активируется каждый раз, когда число попаданий кратно 4.  
  
## <a name="remarks"></a>Примечания  
 Используется для `stylePassCount` членом [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) структуру, которая в свою очередь является членом [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
