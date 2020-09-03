---
title: 'IDebugProgramEngines2:: Енумпоссиблингинес | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a417fd4f0d90ffebd291179dee28a0e81f92cce9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182190"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает идентификаторы GUID для всех возможных модулей отладки (DE), которые могут отлаживать эту программу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```csharp  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celtBuffer`  
 окне Число возвращаемых ИДЕНТИФИКАТОРов DE. Это также указывает максимальный размер `rgguidEngines` массива.  
  
 `rgguidEngines`  
 [вход, выход] Массив ИДЕНТИФИКАТОРов DE, которые необходимо заполнить.  
  
 `pceltEngines`  
 заполняет Возвращает фактическое число возвращаемых ИДЕНТИФИКАТОРов DE.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` или [C#] 0x8007007A, если буфер недостаточно велик.  
  
## <a name="remarks"></a>Remarks  
 Чтобы определить, сколько ядер существует, вызовите этот метод один раз, указав `celtBuffer` для параметра значение 0, а для `rgguidEngines` параметра задается NULL. Этот метод возвращает `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A для C#), а `pceltEngines` параметр возвращает необходимый размер буфера.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
