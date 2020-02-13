---
title: Создание моделей для приложения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.commentlink.properties
- vs.teamarch.UMLModelExplorer.dependency
- vs.teamarch.UMLModelExplorer.commentlink
- vs.teamarch.common.dependency.properties
- Microsoft.VisualStudio.Uml.Diagrams.CommentShape.IsTransparent
- vs.teamarch.common.comment.properties
- vs.teamarch.UMLModelExplorer.comment
helpviewer_keywords:
- diagrams - modeling, sequence
- software design
- diagrams - modeling, use case
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML model
- diagrams - modeling, UML use case
- diagrams - modeling, class
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- software modeling
- diagrams - modeling, UML sequence
- UML
- diagrams - modeling, UML
- diagrams - modeling, layer
- software, designing
- diagrams - modeling, UML class
- software, modeling
- UML diagrams
ms.assetid: b69d9d91-c7e7-4dee-8eb6-706076eecb85
caps.latest.revision: 60
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7e1b37a357113be010ea336fc5666beb8cd33dbc
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852010"
---
# <a name="create-models-for-your-app"></a>Создание моделей для приложения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Схемы моделирования помогают понять, уточнить и передать другим сведения о коде и пользовательских требованиях, которым должна удовлетворять ваша программная система. Например, для описания и передачи пользовательских требований можно использовать схемы UML вариантов использования, деятельности, классов и последовательностей. Для описания функциональных возможностей системы и передачи сведений о них можно использовать схемы UML компонентов, классов, деятельности и последовательностей.

 См. [видео Channel 9: улучшение архитектуры с помощью моделирования](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling).

 В этом выпуске можно создавать следующие UML-схемы:

|**Схема**|**Что показывает**|
|-----------------|---------------|
|[UML-схемы деятельности: справочные материалы](../modeling/uml-activity-diagrams-reference.md)|Поток работы между действиями и участниками в рамках бизнес-процесса|
|[Схемы компонентов UML: справочные материалы](../modeling/uml-component-diagrams-reference.md)|Компоненты системы, их интерфейсы, порты и отношения|
|[UML-схемы классов: справочные материалы](../modeling/uml-class-diagrams-reference.md)|Типы, используемые для хранения данных  и их отношений и обмена ими в системе|
|[UML-схемы последовательностей: справочные материалы](../modeling/uml-sequence-diagrams-reference.md)|Последовательности взаимодействий между объектами, компонентами, системами или субъектами|
|[UML-схемы вариантов использования: справочные материалы](../modeling/uml-use-case-diagrams-reference.md)|Цели и задачи пользователей, поддерживаемые системой|

 Чтобы узнать, какие версии Visual Studio поддерживают каждый тип схемы, см. раздел [Поддержка версий для инструментов архитектуры и моделирования](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Для визуализации архитектуры системы или имеющегося кода создайте следующие схемы:

|**Схема**|**Что показывает**|
|-----------------|---------------|
|[Схемы слоев: рекомендации](../modeling/layer-diagrams-guidelines.md)<br /><br /> [Схемы слоев: справочные материалы](../modeling/layer-diagrams-reference.md)|Высокоуровневая архитектура системы|
|Карты кода<br /><br /> [Сопоставление зависимостей во всех решениях](../modeling/map-dependencies-across-your-solutions.md)<br /><br /> [Поиск потенциальных проблем с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)|Зависимости и другие отношения в имеющемся коде|
|Схемы классов, созданные кодом<br /><br /> [Работа со схемами классов (конструктор классов)](../ide/working-with-class-diagrams-class-designer.md)|Типы и их отношения в коде .NET|

## <a name="common-tasks"></a>Общие задачи

|**статья**;|**Задача**|
|---------------|--------------|
|[Создание проектов и схем моделирования UML](../modeling/create-uml-modeling-projects-and-diagrams.md)|**Создание моделей** и Добавление схем.|
|[Изменение моделей и схем UML](../modeling/edit-uml-models-and-diagrams.md)|Для изменения модели **Нарисуйте диаграммы** .|
|[Определение пакетов и пространств имен](../modeling/define-packages-and-namespaces.md)|**Создание пакетов** для разделения модели на единицы, над которыми могут работать различные члены группы.|
|[Создание кода на основе схем классов UML](../modeling/generate-code-from-uml-class-diagrams.md)|**Создайте C# код на основе схем классов** , чтобы начать реализацию.|
|[Настройка модели с помощью профилей и стереотипов](../modeling/customize-your-model-with-profiles-and-stereotypes.md)|**Настройка элементов модели** с помощью стереотипов для расширения стандартных элементов модели UML для конкретных целей.|
|[Связывание элементов модели и рабочих элементов](../modeling/link-model-elements-and-work-items.md)|**Создавайте связи между элементами модели и рабочими элементами** , чтобы контролировать задачи, тестовые случаи, ошибки, требования, проблемы или другие виды работы, связанные с определенными частями модели.|
|[Экспорт схем в виде изображений](../modeling/export-diagrams-as-images.md)|**Сохраните модель и схемы** , чтобы предоставить общий доступ другим пользователям, включая тех, кто не использует [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].|

## <a name="related-tasks"></a>Связанные задачи

|**статья**;|**Задача**|
|---------------|--------------|
|[Визуализация кода](../modeling/visualize-code.md)|Создавайте карты кода и схемы слоев, чтобы лучше разобраться в незнакомом коде.|
|[Моделирование требований пользователей](../modeling/model-user-requirements.md)|Используйте модели для уточнения потребностей пользователей и передачи информации о них.|
|[Моделирование архитектуры приложения](../modeling/model-your-app-s-architecture.md)|Используйте модели, чтобы описать общую структуру и поведение системы, а также обеспечить ее соответствие потребностям пользователей.|
|[Проверка системы в ходе разработки](../modeling/validate-your-system-during-development.md)|Убедитесь, что программное обеспечение соответствует потребностям пользователей и общей архитектуре системы.|
|[Использование моделей в процессе разработки](../modeling/use-models-in-your-development-process.md)<br /><br /> [Использование моделей в гибкой разработке](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)|Используйте модели, чтобы изучить и изменить систему во время разработки.|
|[Разработка структуры решения моделирования](../modeling/structure-your-modeling-solution.md)|Упорядочивайте модели в рамках проекта большого или среднего размера.|

## <a name="external-resources"></a>Внешние ресурсы

|**Категория**|**Links**|
|------------------|---------------|
|**Форумы**|-   [Средства моделирования и визуализации Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Пакет SDK для моделирования и визуализации в Visual Studio (инструменты DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
