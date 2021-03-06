---
title: -NoSplash (devenv.exe)
description: Узнайте, как использовать параметр командной строки NoSplash devenv, чтобы запретить отображение экрана-заставки.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e86398663ea7b6c8209d4123ab3cb12651d4491e
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96044002"
---
# <a name="nosplash-devenvexe"></a>/NoSplash (devenv.exe)

Отключает отображение экрана-заставки.

## <a name="syntax"></a>Синтаксис

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>Аргументы

- *File1*

  Необязательный параметр. Файл, открываемый в существующем экземпляре Visual Studio. Если экземпляр Visual Studio отсутствует, в упрощенном окне создается новый экземпляр, в котором открывается *File1*.

- *FileN*

  Необязательный параметр. Один или несколько дополнительных файлов для открытия в существующем экземпляре Visual Studio.

## <a name="remarks"></a>Комментарии

Этот параметр скрывает экран-заставку. Если этот параметр не задан, экран-заставка отображается. Для отображения экрана-заставки в дальнейшем (например, для проверки логотипа продукта VSPackage) необходимо использовать параметр [/Splash](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

Параметр `/NoSplash` можно использовать вместе с другими параметрами, например [/Run](run-devenv-exe.md) или [/DebugExe](debugexe-devenv-exe.md).

## <a name="example"></a>Пример

Все три примера запускают интегрированную среду разработки без отображения экрана-заставки. Второй пример также компилирует указанное решение и запускает созданный исполняемый файл. Третий пример открывает указанный исполняемый файл открывается для отладки в интегрированной среде разработки.

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [Параметры командной строки Devenv для разработки VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
