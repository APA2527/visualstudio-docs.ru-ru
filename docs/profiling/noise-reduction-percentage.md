---
title: Процент снижения шума | Документы Майкрософт
description: Сведения о параметре "Процент снижения шума" и способах управления количеством записей, отображаемых в дереве вызовов.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.filter
helpviewer_keywords:
- Concurrency Visualizer, Noise Reduction Percentage
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f5e743210cebfc904c88c8f45e772db9beeda40
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722858"
---
# <a name="noise-reduction-percentage"></a>Процент снижения шума
По умолчанию процентное значение снижения шума равно 2. В дереве вызовов отображаются только те записи, процент инклюзивного времени которых больше или равен значению этого параметра. Изменяя это значение, можно управлять числом записей, отображаемых в дереве вызовов. Например, при изменении значения на 10 в дереве вызовов будут отображаться только те записи, инклюзивное время которых больше или равно 10 %. Увеличив значение этого параметра, можно сосредоточиться на записях, которые наиболее ощутимо влияют на производительность процесса.