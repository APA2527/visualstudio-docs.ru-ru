---
title: Создание многоэкземплярного окна инструментов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9c31f1c439db69b3795d789758b0604a539ef81
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341631"
---
# <a name="create-a-multi-instance-tool-window"></a>Создание многоэкземплярного окна инструментов
Окно инструментов можно программировать таким образом, чтобы несколько экземпляров могут быть открыты одновременно. По умолчанию окна инструментов может иметь только один экземпляр открыть.

При использовании многоэкземплярного окна инструментов, можно отобразить несколько связанных источников информации, в то же время. Например, можно поместить несколько строк <xref:System.Windows.Forms.TextBox> контролировать многоэкземплярного окна инструментов, таким образом, чтобы несколько фрагментов кода одновременно доступны во время программирования сеанса. Кроме того, к примеру, можно поместить <xref:System.Windows.Forms.DataGrid> управления и стрелку раскрывающегося списка в поле многоэкземплярного окна инструментов, чтобы одновременно может отслеживаться несколько источников данных в реальном времени.

## <a name="create-a-basic-single-instance-tool-window"></a>Создание базового (единственной) окна инструментов

1. Создайте проект с именем **MultiInstanceToolWindow** с помощью шаблона VSIX и добавление шаблона элемента окна пользовательского инструмента с именем **MIToolWindow**.

    > [!NOTE]
    > Дополнительные сведения о создании расширения с окном инструментов, см. в разделе [создание расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="make-a-tool-window-multi-instance"></a>Сделать экземпляр несколькими окна инструментов

1. Откройте *MIToolWindowPackage.cs* файл и найдите `ProvideToolWindow` атрибута. и `MultiInstances=true` параметра, как показано в следующем примере:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. В *MIToolWindowCommand.cs* найдите `ShowToolWindos()` метод. В этом методе, вызывать <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> метод и набор его `create` флаг `false` таким образом, чтобы он будет использовать перебор существующих экземпляров окна инструментов до является доступным `id` найден.

3. Чтобы создать экземпляр окна инструментов, вызовите <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> метод и задайте его `id` доступное значение и его `create` флаг `true`.

    По умолчанию значение `id` параметр <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> метод `0`. Это значение делает окно инструментов с единственным экземпляром. Для более чем один экземпляр для размещения, каждый экземпляр должен иметь свой собственный уникальный `id`.

4. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объект, возвращаемый <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> свойства экземпляра окна инструментов.

5. По умолчанию `ShowToolWindow` метод, который создается с помощью шаблона элемента окна инструментов создает окно инструментов с единственным экземпляром. В следующем примере показано, как изменить `ShowToolWindow` метод для создания нескольких экземпляров.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        for (int i = 0; i < 10; i++)
        {
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);
            if (window == null)
            {
                // Create the window with the first free ID.
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);
                if ((null == window) || (null == window.Frame))
                {
                    throw new NotSupportedException("Cannot create tool window");
                }

            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());
            break;
            }
        }
    }
    ```
