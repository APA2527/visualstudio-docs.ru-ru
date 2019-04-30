---
title: 'Ошибка: Смешанный режим отладки для x64 процессов поддерживается только в том случае, если с помощью Microsoft .NET Framework 4 или более поздней версии | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1423cbcfcae53948f7b9c9cd52eb90f57251bc24
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851056"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Ошибка: Отладка в смешанном режиме для процессов x64 поддерживается только при использовании платформы Microsoft .NET Framework 4 или выше
Для отладки смеси управляемого и неуправляемого кода в 64-разрядном процессе необходимо использовать версию 4 платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Отладка в смешанном режиме для 64-разрядных процессов при использовании версий [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], предшествующих версии 4, не поддерживается.

### <a name="to-correct-this-error"></a>Исправление ошибки

- Выполните одно из следующих действий.

  - Обновите [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] до версии 4.

  - Постройте для отладки 32-разрядную версию приложения.

## <a name="see-also"></a>См. также
- [Remote Debugging](../debugger/remote-debugging.md)