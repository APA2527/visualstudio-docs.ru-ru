---
title: Интерфейс IDispError | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85704ed9e9a9493ef02e4d4d68a84a2d1623533f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446858"
---
# <a name="idisperror-interface"></a>Интерфейс IDispError
Предоставляет подробные контекстные сведения об ошибке.  
  
> [!NOTE]
> Этот интерфейс не реализован.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDispError` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Извлекает определенный тип сведений об ошибке.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Извлекает следующий `IDispError` объекта.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Получает код ошибки из `IDispError` объекта.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Возвращает программный идентификатор зависит от языка для класса или приложения, в котором возникла ошибка.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Возвращает путь к файлу справки и идентификатор раздела справки, который описывает ее, если это возможно.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Возвращает текстовое описание ошибки.|