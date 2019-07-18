---
title: IDebugField | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8bc18204d3cbe20635ab0680a50b4d1555dce2ce
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690306"
---
# <a name="idebugfield"></a>IDebugField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет поле, то есть описание символа или тип.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Символ поставщик реализует этот интерфейс как базовый класс для всех полей.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Этот интерфейс является базовым классом для всех полей. На основе возвращаемого значения из [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), этот интерфейс может возвращать более специализированных интерфейсов с помощью [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3). Кроме того, многие интерфейсы возвращают `IDebugField` объекты из различных методов.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugField`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Получает отображаемую информацию о символ или типа.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Возвращает тип поля.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Возвращает тип поля.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Возвращает контейнер поля.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Возвращает адрес поля.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Получает размер поля в байтах.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Возвращает расширенные сведения о поле.|  
|[Equal](../../../extensibility/debugger/reference/idebugfield-equal.md)|Сравнивает два поля.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Получает сведения зависят от типов символов или типа.|  
  
## <a name="remarks"></a>Примечания  
 Язык C эквивалентен типу `typedef`.  
  
 В следующем примере язык C++ `weather` является типом класса и `sunny` и `stormy` представляют собой символы:  
  
```cpp#  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Поле представляет символ ли тип можно определить путем вызова [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) и изучив [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) результат. Если `FIELD_KIND_TYPE` установлен бит, поле имеет тип и если `FIELD_KIND_SYMBOL` бит устанавливается, он является символьным.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
