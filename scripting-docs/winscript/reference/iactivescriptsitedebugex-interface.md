---
title: Интерфейс IActiveScriptSiteDebugEx | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 605505d101611dfe39835671b042852eab5ca9cb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992387"
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx — интерфейс

Реализуйте этот интерфейс, вместе с `IActiveScriptSiteDebug` интерфейс при создании узла, который должен получать уведомление об ошибке времени выполнения в приложении и при необходимости подключения к приложению для отладки. Диспетчер отладки процессов предоставляет уведомления через `IActiveScriptDebug` при отладчик сценариев Just-In-Time находится на компьютере. Если отладчик сценариев не Just-In-Time является найден, PDM обеспечивает уведомление через `IActiveScriptDebugEx` вместо этого.

Чтобы получить уведомление об ошибке времени выполнения, необходимо обрабатывать узла `ActiveScriptSiteDebug::OnScriptErrorDebug`. На основании действий пользователя, затем можно присоединить внутренний отладчик и возврата или возврата его запуск отладчика в OnScriptErrorDebug `pfEnterDebugger` параметра.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable

|Метод|Описание|
|------------|-----------------|
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Информирует приложение о ошибки времени выполнения скрипта при процесс отладки Manager не удается найти во внешнем отладчике Just In Time.|