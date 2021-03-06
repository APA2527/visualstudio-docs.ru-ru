---
title: 'IDebugDocumentTextEvents2:: Онремоветекст | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnRemoveText
helpviewer_keywords:
- IDebugDocumentTextEvents2::onRemoveText
ms.assetid: 1ebeabb2-52a1-4ccc-83cd-9ae7c3541783
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: abe3942ec83136aca313562bc45e156b123fdf19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903995"
---
# <a name="idebugdocumenttextevents2onremovetext"></a>IDebugDocumentTextEvents2::onRemoveText
Уведомляет пакет отладки, что текст был удален из документа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT onRemoveText( 
   TEXT_POSITION pos,
   DWORD         dwNumToRemove
);
```

```csharp
int onRemoveText( 
   enum_TEXT_POSITION pos,
   uint               dwNumToRemove
);
```

## <a name="parameters"></a>Параметры
`pos`\
окне Структура [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , указывающая место удаления текста.

`dwNumToRemove`\
окне Указывает количество символов в тексте, которые были удалены.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
