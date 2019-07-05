---
title: IActiveScriptAuthor::AddNamedItem | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95bc529db8129c4e9af1ed9f9dc3d91de9686223
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411394"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Добавляет имя элемента корневого уровня в скрипт создания механизма пространства имен. Объект *элемент корневого уровня* — это объект, который может содержать свойства и методы, а, может также содержать источник события.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszName`  
 [in] Имя элемента, как видно из скрипта. Имя должно быть уникальным и является сохраняемым.  
  
 `dwFlags`  
 [in] Флаги, связанные с именованным элементом. Может быть сочетанием следующих значений:  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Указывает, что имя элемента в пространстве имен скрипта. Это позволяет доступ к свойствам элемента, методы и события.<br /><br /> По соглашению свойства элемента включают дочерних элементов элемента. Таким образом все свойства дочерних элементов объекта и методы (и их дочерних элементов, рекурсивно) доступны.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Указывает события источника элемента, что сценарии можно использовать обработчики событий в скрипт.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Указывает, что элемент является коллекцию глобальных свойств и методов, которые связаны со скриптом. Его члены создаются как глобальные переменные и методы.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Указывает, что элемент должен быть сохранен при сохранении сценария разработки ядра.|  
|SCRIPTITEM_CODEONLY|0x00000200|Указывает, что именованный элемент представляет объект только в коде и не предоставляет членом автору.|  
|SCRIPTITEM_NOCODE|0x00000400|Указывает, что именованный элемент — это просто имя добавляемого, и он не имеет ничего общего автору.|  
  
 `pdisp`  
 [in] `IDispatch` Из `NamedItem` объект, который используется для сбора, методы, свойства или источника события.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)