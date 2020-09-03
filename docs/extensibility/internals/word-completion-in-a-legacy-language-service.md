---
title: Завершение слов в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 948751cde5b6b710d911a30ca26a61e5411bba4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703166"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Завершение машинных слов в языковой службе прежних версий
При заполнении слова отсутствующие символы заполняются частично типизированным словом. Если существует только одно возможное завершение, слово завершается после ввода символа завершения. Если частичное слово совпадает с более чем одной возможностью, отображается список возможных завершений. Символом завершения может быть любой символ, который не используется для идентификаторов.

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [расширение редактора и языковых служб](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

## <a name="implementation-steps"></a>Шаги реализации

1. Когда пользователь выбирает пункт **завершить слово** в меню **IntelliSense** , <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> команда отправляется в языковую службу.

2. <xref:Microsoft.VisualStudio.Package.ViewFilter>Класс перехватывает команду и вызывает <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод с причиной синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> .

3. <xref:Microsoft.VisualStudio.Package.Source>Затем класс вызывает метод, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> чтобы получить список возможных завершений слов, а затем отображает слова в списке подсказок с помощью <xref:Microsoft.VisualStudio.Package.CompletionSet> класса.

    Если имеется только одно совпадающее слово, <xref:Microsoft.VisualStudio.Package.Source> класс завершает слово.

   Кроме того, если средство проверки возвращает значение триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> при вводе первого символа идентификатора, <xref:Microsoft.VisualStudio.Package.Source> класс обнаруживает это и вызывает <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод с причиной синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> . В этом случае средство синтаксического анализа должно обнаружить наличие символа выбора элемента и предоставить список элементов.

## <a name="enabling-support-for-the-complete-word"></a>Включение поддержки для полного слова
 Чтобы включить поддержку автозаполнения слов, задайте `CodeSense` именованный параметр, передаваемый <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> атрибуту пользователя, связанному с языковым пакетом. При этом задается <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.

 Средство синтаксического анализа должно возвращать список объявлений в ответ на значение причины синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> , для работы с завершением слов.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Реализация полного слова в методе Парсесаурце
 Для завершения слов <xref:Microsoft.VisualStudio.Package.Source> класс вызывает <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> метод <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса для получения списка возможных совпадений слов. Необходимо реализовать список в классе, производном от <xref:Microsoft.VisualStudio.Package.Declarations> класса. Дополнительные <xref:Microsoft.VisualStudio.Package.Declarations> сведения о методах, которые необходимо реализовать, см. в классе.

 Если список содержит только одно слово, то <xref:Microsoft.VisualStudio.Package.Source> класс автоматически вставляет это слово вместо частичного слова. Если список содержит более одного слова, <xref:Microsoft.VisualStudio.Package.Source> класс представляет список подсказок, из которого пользователь может выбрать подходящий вариант.

 Также взгляните на пример <xref:Microsoft.VisualStudio.Package.Declarations> реализации класса в области [завершения членов в языковой службе прежних версий](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
