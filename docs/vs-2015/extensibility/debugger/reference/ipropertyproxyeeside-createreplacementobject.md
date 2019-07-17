---
title: IPropertyProxyEESide::CreateReplacementObject | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3a21e640d6661f8066609bdc344299ccbd63d52
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68147495"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает копию объекта данных, относящиеся к вычислитель выражений (EE).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dataIn`  
 [in] [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) объект, содержащий данные для копирования.  
  
 `dataOut`  
 [out] Возвращает новый `IEEDataStorage` объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод предоставляется [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) объект, представляющий массив байтов. Это входящий объект данных обычно не реализуют EE. Тем не менее, объект, возвращаемый этим методом всегда реализуется EE, которая позволяет реализовать EE `IEEDataStorage` интерфейс требуется любой класс.  
  
 Обратите внимание на то, что данные предоставляются во входящем `IEEDataStorage` объект должен иметь те же данные в исходящий `IEEDataStorage` объекта.  
  
## <a name="see-also"></a>См. также  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
