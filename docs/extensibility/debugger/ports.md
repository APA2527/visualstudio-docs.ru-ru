---
title: Порты | Документация Майкрософт
description: В этой статье описывается определение и роль порта в архитектуре отладчика в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f13ca62f841525ef91ac7d66b67c09da54cabeb3
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606567"
---
# <a name="ports"></a>Порты
В архитектуре отладчика *порт*:

- — Это контейнер для набора процессов, выполняющихся на сервере. Например, порт может представлять подключение к устройству на основе Windows CE по последовательному кабелю или сетевому компьютеру, не являющемуся DCOM. Один специальный порт, называемый локальным портом, содержит все процессы, запущенные на локальном компьютере.

- Может идентифицировать себя по имени или идентификатору.

- Может перечислить все процессы, запущенные в порте, и запустить и завершить эти процессы.

- Представляется интерфейсом [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , который создается путем передачи аргумента [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) в [аддпорт](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет порт по умолчанию, который обрабатывает все процессы на основе Windows, как собственные, так и управляемые. Пользовательский порт должен быть настроен для подключений внешних устройств, которые не основаны на Windows. Для предоставления таких пользовательских портов необходимо также настроить настраиваемого поставщика портов.

## <a name="see-also"></a>См. также
- [Серверы](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Процессы](../../extensibility/debugger/processes.md)
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
