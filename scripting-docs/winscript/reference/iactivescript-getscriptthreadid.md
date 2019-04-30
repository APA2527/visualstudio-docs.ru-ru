---
title: IActiveScript::GetScriptThreadID | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d329e08e6a17d9edcdf26e14b468c3c56f036c00
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935696"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Извлекает определенный сценариев ядра-идентификатор для потока, связанного с данного потока Win32.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwWin32ThreadID` ,  
 [in] Идентификатор потока, выполняющийся поток Win32 в текущем процессе. Используйте [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) функции для получения идентификатора потока текущим выполняемым потоком.  
  
 `pstidThread` ,  
 [out] Адрес переменной, которая получает идентификатор потока сценарий, связанный с данной потоком Win32. Интерпретация этого идентификатора остается на обработчик скриптов, но это может быть просто копию идентификатор потока Windows. Обратите внимание, что, если поток Win32 завершился, этот идентификатор становится неназначенные, а впоследствии может быть назначен другому потоку.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не была загрузки или инициализации) и поэтому не удалось.|  
  
## <a name="remarks"></a>Примечания  
 Полученный идентификатор может использоваться в последующих вызовах методов управления выполнения поток скрипта например [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) метод.  
  
 Этот метод может вызываться из потоков не основной не входили в выноске отличные от базовых объектов узла или [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) интерфейс.  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)