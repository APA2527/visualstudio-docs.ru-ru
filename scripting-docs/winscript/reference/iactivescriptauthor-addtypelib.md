---
title: 'Иактивескриптаусор:: Аддтипелиб | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddTypeLib
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f4bbcc694b24ffafd4333f635c7cdf0c67793a7
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985342"
---
# <a name="iactivescriptauthoraddtypelib"></a>IActiveScriptAuthor::AddTypeLib
Добавляет библиотеку типов в пространство имен для скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `rguidTypeLib`  
 окне CLSID (идентификатор класса) добавляемой библиотеки типов.  
  
 `dwMajor`  
 окне Основной номер версии.  
  
 `dwMinor`  
 окне Дополнительный номер версии.  
  
 `dwFlags`  
 окне Не используется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод вызывает `LoadTypeLib` для загрузки библиотеки типов. После успешного выполнения этот метод вызывает `IActiveScriptAuthor::AddNamedItem` для добавления сведений о типе.  
  
## <a name="see-also"></a>См. также  
   [интерфейса иактивескриптаусор](../../winscript/reference/iactivescriptauthor-interface.md)  
 [Иактивескриптаусор:: AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)    
 [лоадтипелиб](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelib)