---
title: 'IDebugCoreServer3:: Креатеинстанцеинсервер | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b76c37d767ae38a33d537a96f9ad8f7087503ed2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909961"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Создает экземпляр модуля отладки на сервере.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
);
```

```csharp
int CreateInstanceInServer(
   string     szDll,
   ushort     wLangID,
   ref Guid   clsidObject,
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Параметры
`szDll`\
окне Путь к библиотеке DLL, реализующей CLSID, указанный в `clsidObject` параметре. Если это так `NULL` , то `CoCreateInstance` вызывается функция com.

`wLangId`\
окне Языковой стандарт модуля отладки. Это значение может быть равно 0, если метод [setlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) не должен вызываться.

`clsidObject`\
окне CLSID создаваемого модуля отладки.

`riid`\
окне Идентификатор интерфейса конкретного интерфейса, который необходимо получить из объекта класса.

`ppvObject`\
[out] `IUnknown` интерфейс из созданного объекта. Приведите или маршалирует этот объект к нужному интерфейсу.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [Pragma](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
