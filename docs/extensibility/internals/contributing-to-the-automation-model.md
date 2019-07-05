---
title: Дополнение к модели автоматизации | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 47e6686c82dcb0272fa9b3b3c4d3b7c73afe4475
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335434"
---
# <a name="contribute-to-the-automation-model"></a>Участие в модели автоматизации
Visual Studio предоставляет набор интерфейсов автоматизации для настройки среды. Модель автоматизации — объектная модель, который позволяет конечным пользователям для создания надстроек Visual Studio и расширения.

 Кроме того это наиболее подходящего для вас, как разработчик VSPackage участвовать в модели автоматизации; Таким образом разрешить конечным пользователям вашего VSPackage для создания надстроек и предоставляют согласованный пользовательский интерфейс модели при использовании пакета VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Согласованность работы конечного пользователя, необходимо выполнить набор рекомендаций по разработке VSPackage, чтобы модель автоматизации для VSPackage следует за идеи в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>Содержание раздела
- [Общие сведения о модели автоматизации](../../extensibility/internals/automation-model-overview.md)

 Определяет модель автоматизации как связанные группы объектов, которые управляют важнейшими областями среде. Этот набор объектов, изображенного на схеме модели автоматизации.

- [Автоматизация для пакетов VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md)

 Рассматриваются два основных способа для предоставления службы автоматизации для VSPackage.

- [Предоставление объектов проекта](../../extensibility/internals/exposing-project-objects.md)

 Предоставляет пошаговые инструкции по созданию объектов определенного VSPackage.

- [Моделирование проекта](../../extensibility/internals/project-modeling.md)

 Для стандартного проекта объекты, необходимые для создания службы автоматизации для нового типа проекта объясняется и демонстрируется путь, который следует за автоматизации проектов. Здесь также приведены Листинги объявления и реализации для классов.

- [Предоставляют события](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Содержит пошаговые инструкции по созданию события для модели автоматизации.

- [Поддержка автоматизации для страницы параметров](../../extensibility/internals/automation-support-for-options-pages.md)

 Описывается, как вернуть объект автоматизации для поддержки свойства VSPackage пользовательских **параметры** диалоговое окно на **средство** меню, расширив `DTE.Properties` объекта.

- [Автоматизация для кода](../../extensibility/internals/providing-automation-for-code.md)

 Объясняет, что создание модели автоматизации для кода не требуется. Тем не менее в этом разделе, который предоставляет полезную информацию в модели кода предоставляется ссылка.

- [Практическое руководство. Автоматизация для Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Объясняет, что предоставление автоматизации является хорошей идеей, всякий раз, когда вы хотите сделать объекты автоматизации доступными в окне и среде уже не предоставить объект готовые службы автоматизации. Описание автоматизации для окон инструментов и окон документов.

- [С помощью модели автоматизации](../../extensibility/internals/using-the-automation-model.md)

 Предоставляет два примера кода, в которых показано, как потребитель автоматизации получает начального проекта, объекты автоматизации.

- [Автоматизация для объектов конфигурации и SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Сведения об автоматизации для объектов конфигурации и SelectedItems.

## <a name="reference"></a>Ссылка
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Представлен пример кода, показывающий, как VSPackage участвует в объектной модели автоматизации DTE. Перечисляются параметры, возвращаемые значения и выбранные "Примечания".
