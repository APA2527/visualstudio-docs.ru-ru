---
title: Включение отладки программы | Документация Майкрософт
description: Узнайте, как запустить модуль отладки или присоединить модуль отладки к существующей программе для отладки программы.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9dd31a9ff81493d0a315efc0ce0b607af0c6e422
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840669"
---
# <a name="enable-a-program-to-be-debugged"></a>Включение отладки программы
Прежде чем модуль отладки (DE) сможет выполнить отладку программы, необходимо сначала запустить DE или присоединить его к существующей программе.

## <a name="in-this-section"></a>Содержание раздела
 [Получение порта](../../extensibility/debugger/getting-a-port.md) Описывает, как получить порт в качестве первого шага, чтобы включить отладку программы.

 [Регистрация программы](../../extensibility/debugger/registering-the-program.md) Описание следующего шага при включении отладки программы: ее регистрация в порте. После регистрации программу можно отлаживать в процессе присоединения или JIT-отладки.

 [Присоединение к программе](../../extensibility/debugger/attaching-to-the-program.md) Описание следующего шага: присоединение отладчика к программе.

 [Присоединение на основе запуска](../../extensibility/debugger/launch-based-attachment.md) Описывает вложение на основе запуска для программы, которое выполняется автоматически при запуске SDM.

 [Отправка необходимых событий](../../extensibility/debugger/sending-the-required-events.md) Пошаговые инструкции по созданию обработчика отладки (DE) и присоединению его к программе.

## <a name="related-sections"></a>Связанные разделы
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md) Определяет модуль отладки (DE) и описывает службы, реализованные через интерфейсы DE, а также способ перехода отладчика между различными операционными режимами.
