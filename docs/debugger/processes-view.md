---
title: Представление процессов | Документация Майкрософт
description: В представлении процессов отображается дерево всех активных процессов в системе. В этой статье приводятся сведения о его содержимом и способах использования, а также приводятся ссылки на дополнительные материалы.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d48be382e222c9ca494237ae6b72bae54bb90d62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891453"
---
# <a name="processes-view"></a>Представление процессов
В представлении процессов отображается дерево всех активных процессов в системе. Здесь указаны идентификаторы процессов и имена модулей. Используйте представление процессов, если вы намерены изучить определенный системный процесс, который обычно соответствует выполняемой программе. Процессы идентифицируются по именам модулей или обозначаются как "системные процессы".

 Microsoft Windows поддерживает выполнение нескольких процессов. Каждый процесс может иметь один или несколько потоков, а с каждым потоком могут быть связаны одно или несколько окон верхнего уровня. Каждое окно верхнего уровня может иметь несколько дочерних окон. Символ "+" (плюс) указывает, что этот уровень свернут. В свернутом представлении каждому процессу соответствует одна строка. Щелкните символ "+", чтобы развернуть такой уровень.

 Используйте представление процессов, если вы намерены изучить определенный системный процесс, который обычно соответствует выполняемой программе. Процессы идентифицируются по именам модулей или обозначаются как "системные процессы". Чтобы найти процесс, сверните дерево и выполните поиск по списку.

## <a name="procedures"></a>Процедуры

#### <a name="to-open-the-processes-view"></a>Открытие представления процессов

1. В меню **Spy** выберите пункт **Процессы**.

   ![Представление процессов в Spy++](../debugger/media/spy--_processes.png "Spy++_Processes") Представление процессов в Spy++

   На рисунке выше показано представление процессов, где развернуты узлы процессов и потоков.

### <a name="in-this-section"></a>В этом разделе
 [Поиск процесса в представлении процессов.](../debugger/how-to-search-for-a-process-in-processes-view.md) Содержит сведения о поиске конкретного процесса в представлении процессов.

 [Отображение свойств процесса](../debugger/how-to-display-process-properties.md) описывает, как отобразить дополнительные сведения о процессе.

### <a name="related-sections"></a>Связанные разделы
 [Представления Spy++](../debugger/spy-increment-views.md). Рассказывает о представлениях Spy++ в виде дерева окон, сообщений, процессов и потоков.

 [Использование Spy++.](../debugger/using-spy-increment.md) Содержит вводные сведения о средстве Spy++ и его использовании.

 [Диалоговое окно "Поиск процесса"](../debugger/process-search-dialog-box.md) используется для поиска узла конкретного процесса в представлении процессов.

 [Диалоговое окно "Свойства потока"](../debugger/process-properties-dialog-box.md) отображает свойства процесса, выбранного в представлении процессов.

 [Справочник по Spy++](../debugger/spy-increment-reference.md) содержит разделы с описанием каждого меню и диалогового окна Spy++.