---
title: Выполнение Transact-SQL завершается без отладки | Документация Майкрософт
ms.date: 11/08/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 660b6c8b1f8d09baf35d3d019fe80d428e9d7525
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871134"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Ошибка: Выполнение Transact-SQL завершается без отладки

Эта ошибка возникает при попытке отладки Transact-SQL или процедуры SQLCLR, если отладчик не получает сообщения об отладке от SQL Server.

Это может быть вызвано проблемами с сетью или SQL Server, но наиболее вероятная причина — проблема с правами доступа.

Принимают участие две учетные записи:

- Учетная запись приложения является учетной записью пользователя, с которой выполняется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Учетная запись соединения — это идентификация, используемая для подключения к SQL Server. Эта учетная запись не обязательно совпадает с удостоверением, с которыми выполняется Visual Studio, как если бы при подключении использовалась аутентификация SQL.

  Для отладки SQL необходимо, чтобы учетная запись приложения соответствовала учетной записи подключения или была учетной записью системного администратора.

  При использовании такой учетной записи SQL, как sa, учетная запись приложения должна быть установлена в SQL Server как учетная запись администратора. По умолчанию администраторы виртуальной машины, на которой выполняется SQL Server, являются администраторами SQL Server.

  Чтобы устранить эту ошибку, необходимо:

  - Проверить установленные параметры прав доступа. Дополнительные сведения см. в разделе [Практическое руководство. Предоставление разрешений на отладку SQL Server](/previous-versions/w1bhybwz(v=vs.100)).

  - Удостовериться в том, что отладка SQL настроена верно.

  - Обратиться за консультацией к администратору сети или администратору базы данных.

## <a name="see-also"></a>См. также

- [Настройка отладки SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Практическое руководство. Предоставление разрешений на отладку SQL Server](/previous-versions/w1bhybwz(v=vs.100))
- [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)