---
title: Выбранное подключение использует неподдерживаемый поставщик базы данных | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: adf0dd7392b492364a286b5984de52b2b4640ae2
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700162"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Выбранное подключение использует неподдерживаемый поставщик базы данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Это сообщение появляется при перетаскивании элементов, не использующих поставщик данных .NET Framework для SQL Server из **обозревателя серверов**/**обозреватель баз данных** на [LINQ to SQL Инструменты Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] поддерживает только данные о соединениях, которые используют .NET Framework Provider для SQL Server. Допустимы только подключения к Microsoft SQL Server или Microsoft SQL Server Database File.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- В [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] из данных о соединениях добавляйте только элементы, которые используют .NET Framework Data Provider for SQL Server.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Data.SqlClient>   
 [Поставщики данных .NET framework](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Пошаговое руководство: Создание классов LINQ to SQL (реляционный конструктор объектов)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)