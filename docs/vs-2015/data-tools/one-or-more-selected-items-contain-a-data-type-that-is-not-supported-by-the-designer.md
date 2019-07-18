---
title: Один или несколько выбранных элементов содержат тип данных, который не поддерживается конструктором | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 42a04d4f3eb75f8ca3a922094e9beb245e6c0ed9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704943"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Один или несколько выбранных элементов содержат тип данных, не поддерживаемый конструктором
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Один или несколько элементов, перетащить из **обозревателя серверов**/**обозреватель баз данных** на [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] содержит тип данных, который не поддерживается [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (например, [Определяемых пользователем типов CLR](https://msdn.microsoft.com/library/9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2)).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1. Создайте представление, которое основано на нужной таблице и которое не включает неподдерживаемый тип данных.  
  
2. Перетащите представление из **обозревателя серверов**/**обозреватель баз данных** в конструктор.  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Пошаговое руководство: Создание классов LINQ to SQL (реляционный конструктор объектов)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
