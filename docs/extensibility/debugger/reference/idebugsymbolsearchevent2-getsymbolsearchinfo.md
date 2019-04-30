---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d917a3f33d0c4339420c048fe20184245bb8dac1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868413"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Вызывается обработчиком событий для получения результатов о процессе загрузки символов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetSymbolSearchInfo(
   IDebugModule3**    pModule,
   BSTR*              pbstrDebugMessage,
   MODULE_INFO_FLAGS* pdwModuleInfoFlags
);
```

```csharp
int GetSymbolSearchInfo(
   IDebugModule3              pModule,
   ref string                 pbstrDebugMessage,
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags
);
```

#### <a name="parameters"></a>Параметры
 `pModule`

 [out] IDebugModule3 объект, представляющий модуль, для которого были загружены символы.

 `pbstrDebugMessage`

 [in, out] Возвращает строку, содержащую все сообщения об ошибках из модуля. Если отсутствуют ошибки, эта строка будет просто содержать имя модуля, но никогда не бывает пустым.

> [!NOTE]
> [C++] `pbstrDebugMessage` не может быть `NULL` и должны быть высвобождены с `SysFreeString`.

 `pdwModuleInfoFlags`

 [out] Сочетание флагов из [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) перечисления, указывающее, были ли загружены символы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Когда обработчик получает [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) событие после попытки загрузить отладочные символы для модуля, обработчик можно вызвать этот метод, чтобы определить результаты эта нагрузка.

## <a name="see-also"></a>См. также
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)