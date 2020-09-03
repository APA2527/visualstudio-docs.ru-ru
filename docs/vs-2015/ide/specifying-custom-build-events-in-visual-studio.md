---
title: Указание настраиваемых событий сборки
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fabbd4dc42ac4f66c7f53b639c6e7ed1f432878c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667130"
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Указание настраиваемых событий построения в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указав пользовательское событие сборки, вы можете автоматически запустить команды перед тем, как сборка запустится или после того, как она завершится. Например, можно запустить BAT-файл до запуска сборки или скопировать новые файлы в папку после выполнения сборки. События сборки запускаются, только если сборка успешно достигает этих точек в процессе сборки.

 Конкретные сведения об используемом языке программирования см. в следующих разделах:

- Visual Basic--[практические указания: Указание событий сборки (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- Visual C# и F# — [Указание событий сборки (C#)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++ — [Указание событий сборки ](https://msdn.microsoft.com/library/788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc).

## <a name="syntax"></a>Синтаксис
 События сборки следуют тому же синтаксису, что и команды DOS, но для упрощения процесса создания событий сборки можно использовать макросы. Список доступных макросов см. в разделе [диалоговое окно "Командная строка события перед сборкой события/после сборки"](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

 Для улучшения результатов воспользуйтесь советами по форматированию:

- Добавьте оператор `call` перед всеми событиями сборки, запускающими BAT-файлы.

     Пример: `call C:\MyFile.bat`

     Пример: `call C:\MyFile.bat call C:\MyFile2.bat`

- Заключите пути к файлам в кавычки.

     Пример (для [!INCLUDE[win8](../includes/win8-md.md)]): "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"

- Разделите несколько команд с помощью разрывов строк.

- При необходимости включите подстановочные знаки.

     Пример: `for %I in (*.txt *.doc *.html) do copy %I c:\`*mydirectory*`\`

    > [!NOTE]
    > Команда `%I` в коде выше должна быть `%%I` в пакетных скриптах.

## <a name="see-also"></a>См. также:
 [Компиляция и сборка](../ide/compiling-and-building-in-visual-studio.md) ["диалогового окна командной строки события и после сборки события перед сборкой"](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) [специальные знаки MSBuild](../msbuild/msbuild-special-characters.md) [Пошаговое руководство: сборка приложения](../ide/walkthrough-building-an-application.md)
