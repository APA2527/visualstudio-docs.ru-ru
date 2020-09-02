---
title: 'Идиадатасаурце:: get_lastError | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3ad0570436dda6ac9ae52325c891b32a563cf6f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547368"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает имя файла для последней ошибки загрузки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 претвал  
 заполняет Возвращает строку, содержащую имя PDB-файла, связанного с последней ошибкой загрузки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает последний код ошибки, вызванный операцией загрузки. Возвращает, `E_INVALIDARG` Если `pRetVal` параметр имеет значение `NULL` .  
  
## <a name="example"></a>Пример  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>См. также:  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
