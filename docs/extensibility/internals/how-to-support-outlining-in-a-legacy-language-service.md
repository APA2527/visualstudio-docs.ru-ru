---
title: Практическое руководство. Поддержка структурирования в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f79f98ede5c28f8e3acb682ebe8f23e4dc4f72e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312040"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Практическое руководство. Поддержка структурирования в языковой службы прежних версий
Структурирование позволяет развернуть или свернуть другой области текста. Способ структурирования используется можно определить по-разному в разных языках. Дополнительные сведения см. в разделе [Структура](../../ide/outlining.md).

 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Чтобы узнать больше о новый способ реализовать структурирование, см. в разделе [Пошаговое руководство: структуризация](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.

 Ниже показано, как для поддержки этой команды для языковой службы.

## <a name="to-support-outlining"></a>Для поддержки структурирование

1. Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> на объект языковой службы.

2. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> на текущий объект сеанса структуры для добавления новых структурные области.

## <a name="robust-programming"></a>Отказоустойчивость
 Когда пользователь выбирает **свернуть в определения** на **структура** меню, интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> в службе языка.

 При вызове этот метод передает интегрированной среды разработки <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> указатель (указатель на текстовый буфер) и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (указатель в текущий сеанс структуры).

 Можно вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> метод для нескольких областей структуры, указав этих регионов в `rgOutlnReg` параметра. `rgOutlnReg` Параметр <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> структуры. Этот процесс позволяет указывать разные характеристики скрытой области, такие как развернут или свернут определенного региона.

> [!NOTE]
> Следите за тем, о скрытии символы новой строки. Скрытый текст должен следовать от начала первой строки до последней символ последней строки в разделе, оставляя видимым последним символом новой строки.

## <a name="see-also"></a>См. также
- [Практическое руководство. Поддержка скрытого текста в языковой службы прежних версий](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Практическое руководство. Расширенная поддержка структурирования в языковой службы прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)