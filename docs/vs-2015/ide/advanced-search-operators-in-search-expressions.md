---
title: Операторы расширенного поиска в выражениях поиска | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6befa20bcda7f30896fb2b04fadefb0eb5f21f8d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408409"
---
# <a name="advanced-search-operators-in-search-expressions"></a>Операторы расширенного поиска в выражениях поиска
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью операторов расширенного поиска, можно уточнить поиск содержимого путем создания более сложных выражений на основе простых. Как показано в следующей таблице, эти операторы ограничивают контекст, в котором выполняется запрос.  
  
> [!WARNING]
> Операторы расширенного поиска вводятся с двоеточием на конце и без промежуточных пробелов перед двоеточием: только так поисковая система сможет распознать их.  
  
|Условие, которое требуется найти|Использовать|Пример|Результат|  
|-------------------|---------|-------------|------------|  
|Термин в заголовке раздела|title:|title:binaryreader|Разделы, содержащие "binaryreader" в заголовках.|  
|Термин в примере кода|code:|code:readdouble|Разделы, содержащие"readdouble" в примере кода.|  
|Термин в примере конкретного языка программирования|code:vb:|code:vb:string|Разделы, содержащие "string", в примере Visual Basic.|  
|Раздел, связанный с конкретным ключевым словом индекса|keyword:|keyword:readbyte|Разделы, связанные с ключевым словом индекса "readbyte"|  
  
 Оператор code: можно использовать для поиска сведений о любом из нескольких языков программирования, но он возвращает результаты только для содержимого, которое включает отметку о конкретном языке программирования. В следующей таблице перечислены языки программирования, которые поддерживает этот оператор.  
  
|Язык программирования|Использовать|  
|--------------------------|---------|  
|Visual Basic|code:vb<br /><br /> или<br /><br /> code:visualbasic|  
|C#|code:c#<br /><br /> или<br /><br /> code:csharp|  
|C++|code:cpp<br /><br /> или<br /><br /> code:c++<br /><br /> или<br /><br /> code:cplusplus|  
|F#|code:f#<br /><br /> или<br /><br /> code:fsharp|  
|JavaScript|code:javascript<br /><br /> или<br /><br /> code:js|  
|XAML|code:xaml|  
  
## <a name="see-also"></a>См. также  
 [Логические операторы в выражениях поиска](../ide/logical-operators-in-search-expressions.md)   
 [Советы по полнотекстовому поиску](../ide/full-text-search-tips.md)
