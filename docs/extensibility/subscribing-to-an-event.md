---
title: Подписка на событие | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c0466d5b8644ddeae60df24b8b980ee9da0f820
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331685"
---
# <a name="subscribing-to-an-event"></a>Подписка на событие
В этом пошаговом руководстве объясняется, как создать окно инструментов, который реагирует на события в таблице выполняющихся документов (RDT). Окно инструментов содержит пользовательский элемент управления, который реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Метод подключает интерфейс к событиям.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Подписка на события RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Создание расширения с окном инструментов

1. Создайте проект с именем **RDTExplorer** с помощью шаблона VSIX и добавление шаблона элемента окна пользовательского инструмента с именем **RDTExplorerWindow**.

     Дополнительные сведения о создании расширения с окном инструментов, см. в разделе [создания расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Подписаться на события RDT

1. Откройте файл RDTExplorerWindowControl.xaml и удаление кнопки с именем `button1`. Добавление <xref:System.Windows.Forms.ListBox> управления и примите имя по умолчанию. Элемент Grid должен выглядеть следующим образом:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Откройте файл RDTExplorerWindow.cs в представлении кода. Добавьте следующие операторы using в начало файла.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Изменить `RDTExplorerWindow` класса, который, помимо наследования от <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> класс, он реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> интерфейс.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Реализуйте расширение <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Реализуйте интерфейс. Поместите курсор на имя IVsRunningDocTableEvents. Вы должны увидеть лампочки в левом поле. Щелкните стрелку вниз справа от лампочки и выберите **реализовать интерфейс**.

5. В каждом методе в интерфейсе, замените строку `throw new NotImplementedException();` с этим:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Добавьте в класс RDTExplorerWindow поле файла cookie.

    ```csharp
    private uint rdtCookie;
    ```

     Содержит файл cookie, который возвращается методом <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> метод.

7. Переопределите метод Initialize() RDTExplorerWindow для регистрации событий RDT. Службы всегда должна появиться в метод Initialize() ToolWindowPane, а не в конструкторе.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> Служба вызывается для получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> интерфейс. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Метод подключается событий RDT для объекта, реализующего <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, в этом случае объект RDTExplorer.

8. Обновите метод Dispose() RDTExplorerWindow.

    ```csharp
    protected override void Dispose(bool disposing)
    {
        // Release the RDT cookie.
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));
        rdt.UnadviseRunningDocTableEvents(rdtCookie);

        base.Dispose(disposing);
    }
    ```

     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> Метод удаляет соединение между `RDTExplorer` и уведомления о событиях RDT.

9. Добавьте следующую строку в текст <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> обработчик, непосредственно перед `return` инструкции.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Добавить как строку в текст <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> обработчика и с другими событиями, которые вы хотите увидеть в списке.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.

12. Откройте **RDTExplorerWindow** (**представления и других Windows / RDTExplorerWindow**).

     **RDTExplorerWindow** откроется окно со списком пустое событие.

13. Откройте или создайте решение.

     Как `OnBeforeLastDocument` и `OnAfterFirstDocument` события запускаются, появится уведомление каждого события в списке.