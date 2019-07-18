---
title: Практическое руководство. Сохранение данных с помощью транзакции
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bf5864d25e78b6050da5c13097503b2998dda44a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566320"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Практическое руководство. Сохранение данных с помощью транзакции

Сохранение данных в транзакции с помощью <xref:System.Transactions> пространства имен. Используйте <xref:System.Transactions.TransactionScope> объекту участвовать в транзакции, которая автоматически осуществляется автоматически.

Проекты не создаются со ссылкой на *System.Transactions* сборки, поэтому необходимо вручную добавить ссылку на проекты, использующие транзакции.

Самый простой способ реализации транзакции является создание экземпляра <xref:System.Transactions.TransactionScope> объекта в `using` инструкции. (Дополнительные сведения см. в разделе [инструкцией](/dotnet/visual-basic/language-reference/statements/using-statement), и [инструкцией](/dotnet/csharp/language-reference/keywords/using-statement).) Код, выполняемый в рамках `using` инструкции участвует в транзакции.

Чтобы зафиксировать транзакцию, вызвать <xref:System.Transactions.TransactionScope.Complete%2A> метод в последнем операторе в с помощью блокируется.

Чтобы откатить транзакцию, исключение до вызова метода <xref:System.Transactions.TransactionScope.Complete%2A> метод.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Чтобы добавить ссылку на файл System.Transactions.dll

1. На **проекта** меню, выберите **добавить ссылку**.

2. На **.NET** вкладке (**SQL Server** вкладку для проектов SQL Server), выберите **System.Transactions**, а затем выберите **ОК**.

     Ссылку на *System.Transactions.dll* добавляется в проект.

## <a name="to-save-data-in-a-transaction"></a>Чтобы сохранить данные в транзакции

- Добавьте код для сохранения данных с помощью инструкции, содержащей транзакции. Ниже показано, как создать и создание экземпляра <xref:System.Transactions.TransactionScope> объекта в с помощью инструкции:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>См. также

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
- [Пошаговое руководство: сохранение данных в транзакции](../data-tools/save-data-in-a-transaction.md)