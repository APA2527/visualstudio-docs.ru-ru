---
title: Создание пользовательских визуализаторов данных | Документация Майкрософт
ms.date: 11/07/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64f44379c98808cb93fbe51498234a34a695c3d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564734"
---
# <a name="create-custom-data-visualizers"></a>Создание пользовательских визуализаторов данных
 *Визуализатор* — это компонент пользовательского интерфейса отладчика [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], который отображает переменную или объект способом, подходящим для этого типа данных. Например, HTML-визуализатор интерпретирует строку HTML и отображает результат в том виде, в каком она будет выглядеть в окне браузера. Визуализатор точечных рисунков распознает структуру точечного рисунка и отображает его. Некоторые визуализаторы позволяют не только просматривать, но и редактировать данные.

 Отладчик [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] включает шесть стандартных визуализаторов. Визуализаторы текста, HTML, XML и JSON работают со строковыми объектами. Визуализатор дерева WPF отображает свойства визуального дерева объекта WPF. Визуализатор набора данных работает с объектами DataSet, DataView и DataTable.

В будущем могут появиться дополнительные визуализаторы, которые будут доступны для загрузки из корпорации Майкрософт, сторонних компаний и сообщества. Кроме того, вы можете создавать собственные визуализаторы и устанавливать их в отладчик [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

В отладчике для обозначения визуализаторов используется значок лупы ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Значок визуализатора"). Можно выбрать значок в **DataTip**, окне **Контрольные значения** отладчика или диалоговом окне **Быстрая проверка**, а затем выбрать подходящий визуализатор для соответствующего объекта.

## <a name="write-custom-visualizers"></a>Создание пользовательских визуализаторов

 > [!NOTE]
 > Сведения о создании пользовательского визуализатора для машинного кода см. в примере [собственного визуализатора отладчика SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer). Пользовательские визуализаторы не поддерживаются для приложений UWP и Windows 8.x.

Пользовательский визуализатор можно создать для объекта любого управляемого класса, за исключением <xref:System.Object> и <xref:System.Array>.

Архитектура визуализатора отладчика состоит из двух частей:

- *Сторона отладчика* выполняется в отладчике Visual Studio и создает и отображает пользовательский интерфейс визуализатора.

- *Сторона отлаживаемого кода* — код, который выполняется внутри процесса, отлаживаемого в Visual Studio (*отлаживаемая* программа). Объект данных для визуализации (например, строковый объект) существует в отлаживаемом процессе. Сторона отлаживаемой программы отправляет объект на сторону отладчика, где он отображается в созданном пользовательском интерфейсе.

Сторона отладчика получает объект данных для визуализации от *поставщика объектов*. В поставщике объектов реализуется интерфейс <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>. Сторона отлаживаемой программы отправляет объект, используя *источник объекта*, который является производным от <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.

Поставщик объектов может также отправлять данные обратно к источнику объекта, что позволяет создавать визуализаторы, которые могут изменять данные. Поставщик объектов может быть переопределен, чтобы контактировать с вычислителем выражений и, следовательно, с источником объектов.

Сторона отлаживаемой программы и сторона отладчика взаимодействуют друг с другом с помощью методов <xref:System.IO.Stream>, выполняющих сериализацию объекта данных в <xref:System.IO.Stream> и десериализацию <xref:System.IO.Stream> обратно в объект данных.

Можно написать визуализатор для универсального типа, только если тип является открытым. Ограничения накладываются те же, что и при использовании атрибута `DebuggerTypeProxy`. Дополнительные сведения см. в статье об [использовании атрибута DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).

При работе с пользовательскими визуализаторами следует учитывать вопросы безопасности. См. статью [Вопросы безопасности визуализатора](../debugger/visualizer-security-considerations.md).

Следующие действия предоставляют общий обзор создания визуализатора. Подробные инструкции см. в статьях [Пошаговое руководство. Создание визуализатора на C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) или [Пошаговое руководство. Создание визуализатора на Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).

### <a name="to-create-the-debugger-side"></a>Создание кода для отладочной стороны

Чтобы создать пользовательский интерфейс визуализатора на стороне отладчика, необходимо создать класс, который наследует <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>, и переопределить метод <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> для отображения интерфейса. Для отображения в визуализаторе форм, диалоговых окон и элементов управления Windows можно использовать интерфейс <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>.

1. Используйте методы <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> для получения визуализированного объекта на стороне отладчика.

1. Создайте класс, который наследует от <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.

1. Переопределите метод <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> для отображения интерфейса. Используйте методы <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> для отображения в интерфейсе форм, диалоговых окон и элементов управления Windows.

4. Примените <xref:System.Diagnostics.DebuggerVisualizerAttribute>, задавая ему визуализатор для отображения (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).

### <a name="to-create-the-debuggee-side"></a>Создание кода для отлаживаемого объекта

Код на стороне отлаживаемой программы задается с помощью <xref:System.Diagnostics.DebuggerVisualizerAttribute>.

1. Используйте <xref:System.Diagnostics.DebuggerVisualizerAttribute>, предоставив ему визуализатор (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) и источник объекта (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Если источник объекта не задан, визуализатор будет использовать источник объекта, заданный по умолчанию.

1. Чтобы разрешить визуализатору изменять и отображать объекты данных, переопределите методы `TransferData` или `CreateReplacementObject` из <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.

## <a name="see-also"></a>См. также

- [Пошаговое руководство: создание визуализатора на C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Пошаговое руководство: создание визуализатора на Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Практическое руководство. Установка визуализатора](../debugger/how-to-install-a-visualizer.md)
- [Практическое руководство. Тестирование и отладка визуализатора](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Справочные сведения о программном интерфейсе визуализаторов](../debugger/visualizer-api-reference.md)
- [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)