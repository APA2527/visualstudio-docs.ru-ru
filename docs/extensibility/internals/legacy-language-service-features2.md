---
title: Устаревший языковой службы Features2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de7e0fa6a229929a34ed3654c3a4e03e02d1129b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333507"
---
# <a name="legacy-language-service-features"></a>Функции службы устаревшего языка
В следующих разделах перечислены некоторые функции устаревший языковой службы, которые можно указать.

 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Чтобы подробнее узнать о новых способах реализации языковой службы, см. в разделе [редактора и языковой службы расширения](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.

## <a name="in-this-section"></a>В этом разделе
- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Объясняется, как реализовать Цветовая подсветка синтаксиса.

- [Автоматическое форматирование в языковой службе прежних версий](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Объясняется, как реализовать автоматическое форматирование.

- [Сведения о параметрах в языковой службе прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Объясняет, как реализовать подсказке сведений о параметрах IntelliSense.

- [Завершение операторов в языковой службе прежних версий](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Объясняется, как для реализации списка операторов IntelliSense и список завершения члена.

- [Структурирование и скрытый текст в языковой службе прежних версий](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Описание способов реализации структуры или скрытого текста.

- [Практическое руководство. Расширенная поддержка структурирования в языковой службе прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Описываются некоторые действия, описанные в реализации поддержки отладчика...

## <a name="related-sections"></a>Связанные разделы