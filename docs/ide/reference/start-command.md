---
title: Команда Start
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f455306a87c82c5cd4fe55ccacdbba070b4467c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926026"
---
# <a name="start-command"></a>Команда Start
Начинает отладку запускаемого проекта.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Аргументы
`address`

Необязательный параметр. Адрес, по которому программа приостанавливает выполнение, сходен с точкой останова в исходном коде. Этот аргумент применяется только в режиме отладки.

## <a name="remarks"></a>Примечания
При запуске команды **Запустить** она выполняет операцию RunToCursor по указанному адресу.

## <a name="example"></a>Пример
Этот пример запускает отладчик и игнорирует все возникающие исключения.

```cmd
>Debug.Start
```

## <a name="see-also"></a>См. также

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)