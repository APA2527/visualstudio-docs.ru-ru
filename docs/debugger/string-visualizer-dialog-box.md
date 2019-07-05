---
title: Диалоговое окно визуализатора строки | Документация Майкрософт
ms.date: 10/10/2018
ms.custom: seoapril2019
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 982db296fd17fb86b4a139e02a9418eeb507cd91
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62902543"
---
# <a name="string-visualizer-dialog-box"></a>Диалоговое окно визуализатора строки

При отладке в Visual Studio, можно просмотреть строки с помощью визуализатора встроенным строковым. Визуализатор строки показаны строки, которые слишком длинны для окна подсказки или отладчик данных. Он также поможет выявить неправильный формат строки.

Включает встроенный строковый визуализатор обычного текста, XML, HTML и JSON параметров. Также можно открыть встроенные визуализаторы для некоторых других типов, таких как [DataSet, DataTable и DataView](../debugger/dataset-visualizer-dialog-box.md) объекты, от **"Видимые"** или других окнах отладчика.

> [!NOTE]
> Если вам нужно проверять элементы XAML или пользовательского интерфейса WPF в средстве визуализации, см. в разделе или [свойства проверять XAML во время отладки](../debugger/inspect-xaml-properties-while-debugging.md) или [Практическое использование визуализатора дерева WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

Чтобы открыть визуализатор строки, должен быть приостановлен во время отладки. Наведите курсор на переменную, которая имеет обычный текст, XML, HTML или JSON строковое значение и щелкните значок лупы ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "значок визуализатор").

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса

**Выражение** поле показывает, переменную или выражение при наведении указателя.

**Значение** поле отображается строковое значение. Пустое **значение** означает, что выбранный визуализатор не может распознать строку. Например **визуализатор XML** показано пустое **значение** строку текста без тегов XML, или строку JSON. Чтобы просмотреть строки, не может распознать выбранного визуализатор, выберите **визуализатор текста** вместо этого. **Визуализатор текста** показан обычный текст.

### <a name="json-string-data"></a>Строковые данные JSON

Правильный формат строки JSON выглядит как на следующем рисунке в визуализатор JSON. Неправильно сформированный JSON может отображать значок ошибки (или остается пустым, если нераспознанный). Чтобы определить ошибку, JSON, скопируйте и вставьте строку в средство анализа кода JSON, такие как [JSLint](https://www.jslint.com/).

![Визуализатор строки JSON](../debugger/media/dbg-tips-string-visualizer-json.png "визуализатор строки JSON")

### <a name="xml-string-data"></a>Строка XML-данных

Правильный формат XML-строку выглядит как на следующем рисунке в визуализаторе XML. Некорректный код XML может отображать без тегов XML либо пуст, если нераспознанный.

![Визуализатор строки XML](../debugger/media/dbg-string-visualizers-xml.png "визуализатор строки XML")

### <a name="html-string-data"></a>Строковые данные HTML

Правильный формат строки HTML отображается так, как если Визуализированный в браузере, как показано на следующем рисунке. Неправильный формат HTML могут отображаться в виде обычного текста.

![HTML-визуализатор строки](../debugger/media/dbg-string-visualizers-html.png "HTML-визуализатор строки")

## <a name="see-also"></a>См. также

- [Создание настраиваемых визуализаторов (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Визуализации данных в Visual Studio для Mac](/visualstudio/mac/data-visualizations)