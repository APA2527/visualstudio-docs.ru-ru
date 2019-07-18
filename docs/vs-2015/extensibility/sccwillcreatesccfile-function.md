---
title: Функция SccWillCreateSccFile | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb0df475098a0fb0675327cece6dd9c643a0c4d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68147951"
---
# <a name="sccwillcreatesccfile-function"></a>Функция SccWillCreateSccFile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция определяет, поддерживает ли подключаемый модуль системы управления версиями Создание MSSCCPRJ. Файл SCC для каждого заданного файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 nFiles  
 [in] Количество имен файлов, включенных в `lpFileNames` массива, а также длину `pbSccFiles` массива.  
  
 lpFileNames  
 [in] Массив полных имен (массив должен быть выделен вызывающим объектом).  
  
 pbSccFiles  
 [in, out] Массив, в которой будут храниться результаты.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Выполнено.|  
|SCC_E_INVALIDFILEPATH|Один из путей в массиве является недопустимым.|  
|SCC_E_NONSPECIFICERROR|Обнаружена неспецифическая ошибка.|  
  
## <a name="remarks"></a>Примечания  
 Эта функция вызывается с помощью списка файлов, чтобы определить, если подключаемый модуль системы управления версиями обеспечивает поддержку в MSSCCPRJ. Файл SCC для каждого заданного файлов (Подробнее о MSSCCPRJ. Файл SCC, см. в разделе [MSSCCPRJ. Файл SCC](../extensibility/mssccprj-scc-file.md)). Можно объявить подключаемых модулей системы управления версиями, обладают ли они возможность создания MSSCCPRJ. Файлы SCC, объявив `SCC_CAP_SCCFILE` во время инициализации. Этот подключаемый модуль возвращает `TRUE` или `FALSE` каждого файла в `pbSccFiles` массива, чтобы указать, какие из заданного файлов имеет MSSCCPRJ. Поддержка SCC. Если подключаемый модуль возвращает успех код из функции, учитываются значения, возвращаемого массива. В случае сбоя массива учитывается.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Файл MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
