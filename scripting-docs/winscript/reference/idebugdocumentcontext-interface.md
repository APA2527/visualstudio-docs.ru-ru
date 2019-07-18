---
title: Интерфейс IDebugDocumentContext | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentContext interface
ms.assetid: 665ee08a-5c6a-4ab1-ab93-de376acc9a74
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df4c8b8639a6d4b232f82cf87fff7b069829cc46
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783198"
---
# <a name="idebugdocumentcontext-interface"></a>Интерфейс IDebugDocumentContext
Предоставляет абстрактное представление части документа, отладка которого выполняется. Для текстовых документов это представление состоит из диапазона позицию символа.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugDocumentContext` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugDocumentContext::GetDocument](../../winscript/reference/idebugdocumentcontext-getdocument.md)|Возвращает документ, содержащий этот контекст.|  
|[IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)|Перечисляет контексты кода, связанный с данным контекстом документа.|