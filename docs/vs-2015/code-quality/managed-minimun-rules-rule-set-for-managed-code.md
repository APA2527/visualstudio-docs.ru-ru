---
title: Набор управляемых правил минимальный правила для управляемого кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fbbbdf8a1ece9a57d0216a6c9b59ac9d2a8ea474
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142220"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>Набор правил "Минимальные правила для управляемого кода"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Минимальные правила общего доступа к управляемых сосредоточиться на наиболее важными проблемами в коде, включая возможные уязвимости безопасности, сбои приложения и другие важные ошибки логики и проектирования. Следует включать этот набор правил во все пользовательские наборы правил, создаваемые для проектов.  
  
|Правило|Описание|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Удалите пустые методы завершения|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Следует высвобождать высвобождаемые поля|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Перегрузите оператор равенства на переопределяющем типе ValueType.Equals|
