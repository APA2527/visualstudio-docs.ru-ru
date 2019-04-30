---
title: IActiveScript::Close | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53b71471ada55751de301391fdcc70387c1bb6c2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935683"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Вызывает обработчик скриптов отказаться от любого текущего загруженного скрипта, теряют свое состояние и освободить все указатели на интерфейс, он имеет к другим объектам, таким образом ввод закрытом состоянии. Приемники событий, текст сразу же выполненного сценария и вызовов макросов, которые уже находятся в процессе выполнения завершены до изменения состояния (использовать [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) отменить выполняющийся поток скрипта). Этот метод должен вызываться путем создания узлов, до выпуска интерфейса для предотвращения проблем циклическая ссылка.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|`S_OK`|Выполнено.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик сценариев уже был в состоянии closed).|  
|`OLESCRIPT_S_PENDING`|Метод был поставлен в очередь успешно, но состояние еще не изменился. При изменении состояния, сайт в тип обратного вызова на [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) метод.|  
|`S_FALSE`|Метод выполнен успешно, но он уже закрыт.|  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)