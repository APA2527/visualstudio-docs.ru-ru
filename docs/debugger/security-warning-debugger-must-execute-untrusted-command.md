---
title: Предупреждение системы безопасности. Отладчик должен выполнить ненадежную команду | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c4ab45feeae409a1951e1a57e964eaaa5963896
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62902588"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Предупреждение системы безопасности. Отладчик должен выполнить команду без доверия
Это диалоговое окно с предупреждением появляется при использовании сервера системы управления версиями. Оно указывает, что команды, которую должен выполнить отладчик для получения исходного кода, нет в списке доверенных команд для сервера системы управления версиями, содержащемся в файле srcsvr.ini. Если это допустимая команда, ее можно добавить в файл srcsvr.ini. В противном случае ее не следует выполнять. Дополнительные сведения см. в разделе [Указание файлов символов (.pdb) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="message-text"></a>Текст сообщения
 **Отладчик должен выполнить эту команду, для которой не установлено доверие, чтобы получить исходный код с сервера системы управления версиями.**

 **Если файл отладочных символов (\*.pdb) получен из ненадежного источника, эта команда может быть недопустимой или опасной.**

 **Вы хотите выполнить эту команду?**

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса
 Текстовое поле команда из PDB-файл для запуска.

 Выполнения позволяют выполнить команду.

 Не нужно запустить, остановить выполнение команды и загрузку файла с исходного сервера.

## <a name="see-also"></a>См. также
- [Указание файлов символов (.pdb) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Безопасность отладчика](../debugger/debugger-security.md)
- [Исходный сервер](/windows/desktop/Debug/source-server-and-source-indexing)