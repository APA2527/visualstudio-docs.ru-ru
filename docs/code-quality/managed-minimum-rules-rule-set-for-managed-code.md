---
title: Набор правил "Минимальные правила для управляемого кода"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: efb282d8876d48d4f8e7eb81963719e2d14e5900
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649258"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Набор правил "Минимальные правила для управляемого кода"

Управляемые минимальные правила касаются наиболее важных проблем в коде, включая потенциальные бреши в системе безопасности, сбои приложений и другие важные ошибки логики и разработки. Включите это правило в набор настраиваемых правил, создаваемых для проектов.

|Правило|Описание|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|
|[CA1821](../code-quality/ca1821.md)|Удалите пустые методы завершения|
|[CA2213](../code-quality/ca2213.md)|Следует высвобождать высвобождаемые поля|
|[CA2231](../code-quality/ca2231.md)|Перегрузка оператора равенства при переопределении `ValueType.Equals`|
