---
title: 'IScriptEntry:: GetText | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetText
ms.assetid: 105b8244-1972-4b39-ac18-965f1f345ef2
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b25c1667f1df7e0394dd2ebfb0fea452da1b47d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575406"
---
# <a name="iscriptentrygettext"></a>IScriptEntry::GetText
Возвращает текст, соответствующий блоку скрипта `IScriptEntry` или исходному коду, содержащемуся в обработчике событий `IScriptScriptlet`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetText(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstr`  
 заполняет Текст в блоке скрипта `IScriptEntry` или исходный код, содержащийся в обработчике событий `IScriptScriptlet`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)