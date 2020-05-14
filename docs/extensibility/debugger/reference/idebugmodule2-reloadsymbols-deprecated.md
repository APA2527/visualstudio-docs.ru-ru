---
title: IDebugModule2::ReloadSymbols_Deprecated Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e776434e17d90cd2c61c926bbf0100a44ecc524b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726916"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
Устаревшее. НЕ ИСПОЛЬЗУЙТЕ. Перезагружает символы для этого модуля.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ReloadSymbols( 
   LPCOLESTR pszUrlToSymbols,
   BSTR*     pbstrDebugMessage
);
```

```csharp
int ReloadSymbols( 
   string     pszUrlToSymbols,
   out string pbstrDebugMessage
);
```

## <a name="parameters"></a>Параметры
`pszUrlToSymbols`\
(в) Путь к магазину символов.

`pbstrDebugMessage`\
(ваут) Возвращает информационное сообщение, например сообщение о состоянии или сообщение об ошибке, отображаемое справа от имени модуля в окне модулей.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Отладка двигателя всегда `E_FAIL`должны вернуться .

## <a name="remarks"></a>Примечания
 Этот метод больше не поддерживается. Вместо этого реализуем метод [LoadSymbols.](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)

## <a name="see-also"></a>См. также
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
