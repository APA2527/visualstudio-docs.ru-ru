---
title: IDebugPointerField | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d92b1b4d6efda1b8f05c594368a05bd833c9f34
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705828"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет тип указателя.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Поставщик символов реализует этот интерфейс для представления указателя.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Используйте [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для получения этого интерфейса из [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс, если [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) возвращает `FIELD_TYPE_POINTER`.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам на `IDebugField` и `IDebugContainerField` интерфейсы, этот интерфейс реализует следующий метод:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) описанием цели указателя.|  
  
## <a name="remarks"></a>Примечания  
 В C/C++ указатель может являться контейнером, если он используется с помощью нотации массива. Например, если `char *pString`, `pString` с типом указателя на `char`. `pString[3]` имеет тип контейнера, который представляет собой указатель на `char` , ссылающийся на четвертый элемент контейнера.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
