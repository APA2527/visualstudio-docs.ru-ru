---
title: Отладка в смешанном режиме для процессов x64 поддерживается только при использовании платформы Microsoft.NET Framework 4 или выше| Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e974269cccb65db66ee59735f7acc5de494e2106
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697834"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>На 64-разрядных платформах Windows отладка в смешанном режиме поддерживается только при использовании платформы Microsoft.NET Framework версии 4.0 или выше
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Версии .NET Framework, предшествующие 4, не поддерживают отладку в смешанном режиме для процессов x64. Это значит, что при выполнении отладки переход из управляемого кода в неуправляемый (как и обратный переход) невозможен.  
  
### <a name="workarounds"></a>Методы обхода проблемы  
  
- Обновить проект так, чтобы в нем использовалась платформа Microsoft .NET Framework версии 4 или позднее.  
  
     –или–  
  
     Вести отладку управляемого и машинного кода в отдельных сеансах отладки.  
  
     –или–  
  
     Вести отладку смешанного кода в 32-разрядном процессе в соответствии со следующими процедурами:  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Изменение платформы на 32-разрядную версию (Visual Basic или C#)  
  
1. В **обозревателе решений** щелкните правой кнопкой мыши на проект и выберите пункт **Свойства**.  
  
2. На страницах свойств выберите вкладку **Компиляция** или **Отладка**.  
  
3. Выберите пункт **Платформа**, а затем в списке платформ выберите элемент "x86".  
  
     По умолчанию компиляторы Visual Basic и С# создают код, который можно использовать на любом ЦП. На 64-разрядном компьютере такие двоичные файлы работают как 64-разрядные процессы. Чтобы использовать 32-разрядный процесс, необходимо выбрать **Win32**, а не **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Изменение платформы на 32-разрядную версию (C или C++)  
  
1. В **Обозревателе решений** щелкните проект правой кнопкой мыши и выберите команду **Свойства**.  
  
2. На страницах свойств нажмите кнопку **Платформа**, а затем в списке платформ выберите элемент "Win32".  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- См. раздел [Настройка отладки SQL](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>См. также:  
 [Отладка 64-разрядных приложений](../debugger/debug-64-bit-applications.md)
