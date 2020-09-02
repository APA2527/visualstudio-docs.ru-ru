---
title: Практическое руководство. Поиск библиотеки DLL, в которой произошел сбой программы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 44ebe042ff6e2507530e4be410e768550e922b44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703630"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Практическое руководство. Поиск библиотеки DLL, в которой произошел сбой программы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ПРИМЕЧАНИЕ
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, в меню "Сервис" выберите команду "Импорт и экспорт параметров". Дополнительные сведения см. [в разделе Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Если приложение аварийно завершает работу при вызове системных DLL или какого-то другого кода, необходимо найти, какие библиотеки DLL были активны в момент возникновения сбоя. Если сбой библиотеки DLL произошел вне данной программы, то его источник можно определить с помощью окна **Модули**.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Чтобы определить место сбоя при помощи окна Модули  
  
1. Запишите адрес, по которому происходит сбой.  
  
2. В меню **Отладка** выберите пункт **Окна**, а затем **Модули**.  
  
3. В окне **Модули** найдите столбец **Адрес**. В случае необходимости воспользуйтесь полосой прокрутки.  
  
4. Нажмите кнопку **Адрес** (вверху столбца), чтобы отсортировать библиотеки DLL по адресам.  
  
5. Просмотрите отсортированный список и найдите библиотеку DLL, чей диапазон адресов содержит адрес точки сбоя.  
  
6. Посмотрите значения в столбцах **Имя** и **Путь**, чтобы узнать имя и путь библиотеки DLL.  
  
## <a name="see-also"></a>См. также:  
 [Руководство. отладка собственных библиотек DLL](../debugger/how-to-debug-native-dlls.md)   
 [Практическое руководство. Использование окна модулей](../debugger/how-to-use-the-modules-window.md)
