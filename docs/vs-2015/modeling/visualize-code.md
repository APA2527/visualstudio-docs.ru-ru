---
title: Визуализация кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2d5803544e4e7279179929c7c04a3792e4dd9318
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68183866"
---
# <a name="visualize-code"></a>Визуализация кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете использовать средства визуализации и моделирования в Visual Studio, чтобы анализировать существующий код и описать приложение. Это позволяет наглядно изучить, как изменения могут повлиять на код, а также оценить работы и риски, возникающие в результате этих изменений. Например:  
  
- Чтобы понять связи в коде, сопоставьте их визуально.  
  
- Для описания архитектуры системы и поддержания кода в согласованном состоянии с конструкцией создайте схемы слоев и проверьте код на соответствие этим схемам.  
  
- Для описания структур классов создайте схемы классов.  
  
- Чтобы смоделировать различные аспекты системы и сообщить информацию о них, нарисуйте схемы UML. Например, можно смоделировать компоненты системы, типы, взаимодействия и процессы.  
  
  Кроме того, эти средства облегчают взаимодействие с другими участниками проекта. Например, можно использовать схемы классов UML для создания общего глоссария для обсуждения системы с заинтересованными лицами проекта, пользователями и членами команды.  
  
  Чтобы узнать, какие версии Visual Studio поддерживают каждую функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="what-do-you-want-to-do"></a>Выберите действие  
  
|||  
|-|-|  
|**Понимание кода и его отношений.**<br /><br /> Установите связи между определенными частями кода.<br /><br /> Получите общие сведения о связях в коде для всего решения.<br /><br /> **Примечание**. В этом выпуске Visual Studio термин *карта кода* используется вместо *граф зависимостей*.|-   [Сопоставление зависимостей во всех решениях](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Поиск потенциальных проблем, с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Сопоставление методов в стеке вызовов при отладке](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|  
|**Анализ структуры классов:**<br /><br /> Визуализируйте структуру классов в проекте путем создания схем классов на основе кода.|[Практическое руководство. Добавление диаграмм классов в проекты (конструктор классов)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|  
|**Описания высокоуровневую структуру системы и проверить код на соответствие этой структуре:**<br /><br /> Опишите высокоуровневую структуру системы и ее предполагаемые зависимости, создав схемы слоев. Проверьте код на соответствие этой структуре, чтобы убедиться в том, что зависимости в коде согласованы с ней.|-   [Создание схем слоев из кода](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Схемы слоев: Справочник по](../modeling/layer-diagrams-reference.md)<br />-   [Схемы слоев: рекомендации](../modeling/layer-diagrams-guidelines.md)<br />-   [Проверка кода по схемам слоев](../modeling/validate-code-with-layer-diagrams.md)|  
|**Связи, требования пользователей и архитектуру:**<br /><br /> Смоделируйте требования пользователей и архитектуру программной системы, нарисовав схемы UML: схемы деятельности, компонентов, классов, последовательностей и вариантов использования.|-   [Создание моделей для приложения](../modeling/create-models-for-your-app.md)<br />-   [Моделирование требований пользователей](../modeling/model-user-requirements.md)<br />-   [Моделирование архитектуры приложения](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
|**Категория**|**Links**|  
|------------------|---------------|  
|**Форумы**|-   [Средства моделирования и визуализации Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Пакет SDK для моделирования и визуализации в Visual Studio (инструменты DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Блоги**|[Блог по Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Технические статьи и журналы**|[Форум MSDN по архитектуре](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>См. также  
 [Сценарий. Изменение проекта с помощью визуализации и моделирования](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)   
 [Анализ и моделирование архитектуры](../modeling/analyze-and-model-your-architecture.md)   
 [Создание моделей для приложения](../modeling/create-models-for-your-app.md)   
 [Моделирование требований пользователей](../modeling/model-user-requirements.md)   
 [Моделирование архитектуры приложения](../modeling/model-your-app-s-architecture.md)   
 [Использование моделей в процессе разработки](../modeling/use-models-in-your-development-process.md)
