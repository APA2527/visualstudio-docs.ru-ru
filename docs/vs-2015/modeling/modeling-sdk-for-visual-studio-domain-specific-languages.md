---
title: Пакет SDK для моделирования — доменные языки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
ms.assetid: 17a531e2-1964-4a9d-84fd-6fb1b4aee662
caps.latest.revision: 79
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0673f7511276799804dc327bab67637f3fc450b7
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850099"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>SDK моделирования для Visual Studio — доменные языки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью пакета SDK моделирования для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (МСДК) можно создавать мощные средства разработки на основе моделей, которые можно интегрировать в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Например, с помощью MSDK создаются средства UML. Таким же образом можно создать одно или несколько определений моделей и интегрировать их в набор средств.

 Ключевой элемент MSDK — определение модели, которая создается для представления концепций в бизнес-сфере. Для модели можно предусмотреть различные дополнительные средства и возможности, например схематическое представление, возможность создания кода и других артефактов, команды преобразования модели и возможность взаимодействия с кодом и другими объектами в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. При разработке модели ее можно объединить с другими моделями и средствами для создания эффективного набора инструментов, предназначенных для разработки.

 MSDK позволяет быстро разработать модель в виде доменного языка (DSL). Разработка начинается с использования специализированного редактора для определения схемы или абстрактного синтаксиса вместе с графической нотацией. На основе этого определения пакет VMSDK создает:

- реализацию модели со строго типизированным интерфейсом API, работающим в магазине на основе транзакций;

- обозреватель с иерархической структурой;

- графический редактор, в котором пользователи могут просматривать модель или ее части, которые вы определяете;

- методы сериализации, сохраняющие ваши модели в доступном для чтения формате XML;

- средства для создания программного кода и других артефактов, использующих шаблон текста.

  Все эти средства можно настраивать и расширять. Расширения интегрируются таким образом, что сохраняются возможности обновления определения доменного языка и повторного создания функций без потери расширений.

## <a name="samples-and-the-latest-information"></a>Примеры и последние сведения
 [Скачайте пакет SDK моделирования для Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148)

 [Примеры](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples) для пакета SDK для моделирования для Visual Studio.

 Руководство по передовым технологиям и устранению неполадок, см. в статье [форум по Visual Studio DSL и расширяемость средств моделирования](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=dslvsarchx).

## <a name="in-this-section"></a>В этом разделе
 [Начало работы с доменными языками](../modeling/getting-started-with-domain-specific-languages.md)

 [Сведения о моделях, классах и отношениях](../modeling/understanding-models-classes-and-relationships.md)

 [Определение доменного языка](../modeling/how-to-define-a-domain-specific-language.md)

 [Настройка и расширение доменного языка](../modeling/customizing-and-extending-a-domain-specific-language.md)

 [Проверка в доменных языках](../modeling/validation-in-a-domain-specific-language.md)

 [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)

 [Создание кода из доменного языка](../modeling/generating-code-from-a-domain-specific-language.md)

 [Общие сведения о коде доменных языков](../modeling/understanding-the-dsl-code.md)

 [Настройка хранилища файлов и XML-сериализации](../modeling/customizing-file-storage-and-xml-serialization.md)

 [Развертывание решений на доменных языках](../modeling/deploying-domain-specific-language-solutions.md)

 [Создание доменного языка на основе Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

 [Создание доменного языка на основе WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

 [Практическое руководство. Расширение конструктора доменного языка](../modeling/how-to-extend-the-domain-specific-language-designer.md)

 [Выпуски Visual Studio, поддерживаемые пакетом SDK визуализации и моделирования](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)

 [Практическое руководство. Перенос доменного языка в новую версию](../modeling/how-to-migrate-a-domain-specific-language-to-a-new-version.md)

 [Справка по API SDK моделирования для Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
