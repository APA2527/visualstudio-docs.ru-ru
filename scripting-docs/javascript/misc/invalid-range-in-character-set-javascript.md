---
title: Недопустимый диапазон в символе задайте (JavaScript) | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1cbfa4de401c2a1dc0626f8f00dbb0bd1bf24408
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007052"
---
# <a name="invalid-range-in-character-set-javascript"></a>Недопустимый диапазон в наборе символов (JavaScript)
Предпринята попытка создать регулярное выражение с диапазоном набора недопустимый символ. Наборов символов должно находиться в диапазоне от одного символа, например, a – z или 0-9; Классы символов, таких как \w нельзя включить в набор символов. Первый символ в диапазоне, также должны следовать после второго знака в диапазоне. Пример:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Используйте только одиночные символы для составления ваш набор символов регулярного выражения и убедитесь, что они находятся в правильном порядке.  
  
## <a name="see-also"></a>См. также  
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярных выражений (JavaScript)](https://msdn.microsoft.com/library/1400241x)