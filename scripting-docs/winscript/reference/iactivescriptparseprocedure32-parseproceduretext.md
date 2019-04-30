---
title: IActiveScriptParseProcedure32::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e772d8276de5528f0aed25278a03725d09edb180
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993401"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
Выполняет синтаксический анализ данного кода процедуры и добавляет процедуру в пространстве имен.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrCode`  
 [in] Адрес текст процедуры для оценки. Интерпретация этой строки зависит от языка скриптов.  
  
 `pstrFormalParams`  
 [in] Адрес имена формальных параметров для процедуры. Имена параметров должны быть разделены с помощью соответствующих разделителей для обработчика скриптов. Имена не должны заключаться в круглые скобки.  
  
 `pstrProcedureName`  
 [in] Адрес имени процедуры, который необходимо проанализировать.  
  
 `pstrItemName`  
 [in] Адрес имени элемента, которое предоставляет контекст, в котором будет вычисляться процедуры. Если этот параметр равен `NULL`, то код вычисляется в глобальном контексте обработчика скриптов.  
  
 `punkContext`  
 [in] Адрес объекта контекста. Этот объект зарезервирован для использования в среде отладки, где такой контекст может быть предоставлен отладчиком для представления активный контекст среды выполнения. Если этот параметр имеет `NULL`, модуль использует `pstrItemName` для определения контекста.  
  
 `pstrDelimiter`  
 [in] Адрес разделитель end из процедуры. Когда `pstrCode` анализируется из потока текста узел обычно использует разделитель, например две одинарные кавычки («), чтобы обнаружить завершение процедуры. Этот параметр задает разделитель, используемый узлом, позволяя обработчик скриптов для предоставления некоторых условного примитивных предварительной обработки (например, замените одинарной кавычки ['] две одинарные кавычки для использования в качестве разделителя). Точный способ (и нужно ли) сценариев делает ядра, использование этих сведений зависит от обработчика скриптов. Присвойте этому параметру значение `NULL` Если узел не используется разделитель для обозначения конца процедуры.  
  
 `dwSourceContextCookie`  
 [in] Определяемый приложением значение, используемое для отладки.  
  
 `ulStartingLineNumber`  
 [in] Отсчитываемый от нуля значение, которое указывает строку, с которой начинается синтаксический анализ.  
  
 `dwFlags`  
 [in] Флаги, связанные с процедурой. Может представлять собой сочетание этих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Указывает, что код в `pstrCode` выражение, которое представляет возвращаемое значение процедуры. По умолчанию код может содержать выражения, список инструкций или любые объекты, в противном случае допустимые в процедуре язык скрипта.|  
|SCRIPTPROC_IMPLICIT_THIS|Указывает, что `this` указатель входит в область процедуры.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Указывает, что родителям `this` указатель, включаются в область процедуры.|  
  
 `ppdisp`  
 [out] Адрес указателя для объекта, содержащий глобальные методы и свойства сценария. Если обработчик скриптов не поддерживает такой объект `NULL` возвращается.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_NOTIMPL`|Этот метод не поддерживается. Обработчик скриптов не поддерживает добавление во время выполнения процедуры в пространстве имен.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов находится в неинициализированном или закрытом состоянии).|  
|`OLESCRIPT_E_SYNTAX`|Произошла Неуказанная синтаксическая ошибка в процедуре.|  
|`S_FALSE`|Обработчик скриптов не поддерживает объект диспетчеризации; `ppdisp` параметр имеет значение `NULL`.|  
  
## <a name="remarks"></a>Примечания  
 Код скрипта не вычисляется во время этого вызова; Вместо этого процедура компилируется в состояние скрипта, где он может вызываться с помощью сценария позже.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)