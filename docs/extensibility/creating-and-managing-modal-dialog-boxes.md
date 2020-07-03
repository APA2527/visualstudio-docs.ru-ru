---
title: Создание модальных диалоговых окон и управление ими | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2f4f296bb155bcde82235d962ae63c8fa4d41d7
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903773"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Создание модальных диалоговых окон и управление ими
При создании модального диалогового окна в Visual Studio необходимо убедиться, что родительское окно диалогового окна отключено во время отображения диалогового окна, а затем снова включить родительское окно после закрытия диалогового окна. Если этого не сделать, может появиться сообщение об ошибке: *Microsoft Visual Studio не может завершить работу, так как открыто модальное диалоговое окно. Закройте активное диалоговое окно и повторите* попытку.

Это делается двумя способами. Рекомендуемый способ, если имеется диалоговое окно WPF, является производным от <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> , а затем вызывается <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> для вывода диалогового окна. В этом случае нет необходимости управлять модальным состоянием родительского окна.

Если диалоговое окно не является WPF или по какой-либо другой причине не удается создать класс диалогового окна из <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> , необходимо получить родительский элемент диалогового окна, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> метод и самостоятельно управлять модальным состоянием. для этого <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> перед отображением диалогового окна вызовите его с параметром 0 (false) и снова вызовите метод с параметром 1 (true) после закрытия диалогового окна.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Создание диалогового окна, производного от Диалогвиндов

1. Создайте проект VSIX с именем **опендиалогтест** и добавьте команду меню с именем **опендиалог**. Дополнительные сведения о том, как это сделать, см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Чтобы использовать <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> класс, необходимо добавить ссылки на следующие сборки (на вкладке "платформа" диалогового окна " **Добавление ссылки** "):

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. В *OpenDialog.CS*добавьте следующую `using` инструкцию:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Объявите класс с именем `TestDialogWindow` , производным от <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> :

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Чтобы можно было максимально увеличить и развернуть диалоговое окно, задайте <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> для параметра и значение <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> true:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. В `OpenDialog.ShowMessageBox` методе замените существующий код следующим:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Выполните сборку и запустите приложение. Должен отобразиться экспериментальный экземпляр Visual Studio. В меню **Сервис** экспериментального экземпляра должна отобразиться команда с именем **Invoke опендиалог**. При нажатии этой команды должно отобразиться диалоговое окно. Вы сможете максимально увеличить и развернуть окно.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Создание и управление диалоговым окном, не производным от Диалогвиндов

1. Для этой процедуры можно использовать решение **опендиалогтест** , созданное в предыдущей процедуре, с теми же ссылками на сборки.

2. Добавьте следующие `using` объявления:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Создайте класс с именем `TestDialogWindow2` , производным от <xref:System.Windows.Window> :

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Добавьте закрытую ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :

    ```
    private IVsUIShell shell;
    ```

5. Добавьте конструктор, который задает ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. В `OpenDialog.ShowMessageBox` методе замените существующий код следующим:

    ```csharp
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));

    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);
    //get the owner of this dialog
    IntPtr hwnd;
    uiShell.GetDialogOwnerHwnd(out hwnd);
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;
    uiShell.EnableModeless(0);
    try
    {
        WindowHelper.ShowModal(testDialog2, hwnd);
    }
    finally
    {
        // This will take place after the window is closed.
        uiShell.EnableModeless(1);
    }
    ```

7. Выполните сборку и запустите приложение. В меню **Сервис** должна отобразиться команда с именем **Invoke опендиалог**. При нажатии этой команды должно отобразиться диалоговое окно.
