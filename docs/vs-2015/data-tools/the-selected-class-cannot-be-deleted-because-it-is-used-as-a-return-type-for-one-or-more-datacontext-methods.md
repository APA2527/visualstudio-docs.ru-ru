---
title: Не удалось удалить выбранный класс, поскольку он используется в качестве возвращаемого типа для одного или нескольких методов DataContext | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 03e1df5398b4a23a1633d4a0fa92fe0bedb830f6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686630"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Выбранный класс невозможно удалить, потому что он используется как возвращаемый тип одного или нескольких методов DataContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Тип возвращаемого значения одного или нескольких методов <xref:System.Data.Linq.DataContext> это выбранный класс сущностей. Удаление класса сущностей, который используется в качестве типа возврата для метода <xref:System.Data.Linq.DataContext>, вызовет ошибку компиляции проекта. Чтобы удалить выбранный класс сущностей, Идентифицируйте методы <xref:System.Data.Linq.DataContext>, которые его используют, и задайте их типам возврата другой класс сущностей.  
  
 Для возврата типов возврата из <xref:System.Data.Linq.DataContext> методы в их исходный тип создан, сначала удалите <xref:System.Data.Linq.DataContext> метод из области методов и потом перетащите объект из **обозревателя серверов** / **Обозреватель баз данных** в конструктор O/R еще раз.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1. Определить <xref:System.Data.Linq.DataContext> методы, которые используются класс сущностей в качестве возвращаемого типа, выбрав <xref:System.Data.Linq.DataContext> метод в методах области, а также проверять **тип возвращаемого значения** свойство в **свойства** окно .  
  
2. Установите **Тип возврата<xref:System.Data.Linq.DataContext> на другой класс сущностей или удалите метод**  из области методов.  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Пошаговое руководство: Создание классов LINQ to SQL (реляционный конструктор объектов)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Практическое руководство. Изменение типа возвращаемого значения метода DataContext (реляционный конструктор объектов)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)
