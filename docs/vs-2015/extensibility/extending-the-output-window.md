---
title: Расширение окна вывода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2788903c60564d501770616fbe3ad2335e60a250
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204427"
---
# <a name="extending-the-output-window"></a>Расширение окна вывода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Вывода** окно — это набор панелей текста для чтения и записи. Visual Studio есть этих встроенных панелей: **Построение**, в какие проекты обмена сообщениями о сборках, и **Общие**, в котором [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] передает сообщения о интегрированной среды разработки. Проекты получить ссылку на **построения** области автоматически посредством <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> методов интерфейса, а также Visual Studio предлагает прямой доступ к **Общие** области через <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> Служба. Помимо встроенных панелей можно создать и управлять собственных настраиваемых панелей.  
  
 Вы можете управлять **вывода** непосредственно через окно <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> интерфейсов. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Интерфейс, который предлагается в <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> службы, определяет методы для создания, извлечения и уничтожение **вывода** области окна. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Интерфейс определяет методы для отображение панелей, скрытие области и управление им текста. Альтернативный способ управления **вывода** – окно <xref:EnvDTE.OutputWindow> и <xref:EnvDTE.OutputWindowPane> объекты в объектной модели автоматизации Visual Studio. Эти объекты инкапсулировать почти все функциональные возможности <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> интерфейсов. Кроме того <xref:EnvDTE.OutputWindow> и <xref:EnvDTE.OutputWindowPane> объекты добавляют некоторые задачу обеспечения высокоуровневой функциональности, чтобы упростить для перечисления **вывода** области окна и извлечение текста из области.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Создание расширения, которое использует область вывода  
 Можно создать расширение, которое выполняет различные аспекты области вывода.  
  
1. Создайте проект VSIX с именем `TestOutput` с помощью команды меню с именем **TestOutput**. Дополнительные сведения см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Добавьте следующие ссылки:  
  
    1. EnvDTE  
  
    2. EnvDTE80  
  
3. В TestOutput.cs, добавьте следующий оператор using:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4. В TestOutput.cs удалите метод ShowMessageBox. Добавьте следующие заглушку метода:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5. В конструкторе TestOutput измените обработчик команд для OutputCommandHandler. Вот часть, которая добавляет команды:  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6. В следующих разделах существуют различные методы, которые демонстрируют различные способы работы с области вывода. Можно вызвать эти методы в тело метода OutputCommandHandler(). Например следующий код добавляет метод CreatePane(), приведенными в следующем разделе.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Создание окно вывода с помощью IVsOutputWindow  
 В этом примере показано, как создать новую **вывода** область окна с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> интерфейс.  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 Если добавить этот метод расширения, заданного в предыдущем разделе, при нажатии кнопки **вызова TestOutput** команды вы должны увидеть **выходные данные** окно с заголовком, — говорит **Показать выходные данные От: CreatedPane** и слова **это в области создания** в самой области.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>Создание окно вывода с помощью OutputWindow  
 В этом примере показано, как создать **вывода** область окна с помощью <xref:EnvDTE.OutputWindow> объекта.  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 Несмотря на то что <xref:EnvDTE.OutputWindowPanes> коллекции позволяет извлекать **вывода** области окна по его названию, названия панели не гарантируется уникальность. Когда вы сомневаюсь, уникальность заголовок, используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> метод для извлечения области правильный по его идентификатору GUID.  
  
 Если добавить этот метод расширения, заданного в предыдущем разделе, при нажатии кнопки **вызова TestOutput** команды, вы увидите окно вывода с заголовком, — говорит **Показать выходные данные из: DTEPane** и слова **добавлены области DTE** в самой области.  
  
## <a name="deleting-an-output-window"></a>Удаление окно вывода  
 В этом примере показан способ удаления **вывода** область окна.  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 Если добавить этот метод расширения, заданного в предыдущем разделе, при нажатии кнопки **вызова TestOutput** команды, вы увидите окно вывода с заголовком, — говорит **Показать выходные данные из: Новая область** и слова **добавлены созданные панели** в самой области. Если щелкнуть **вызова TestOutput** команду еще раз, область удаляется.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Начало области "Общие" окна вывода  
 В этом примере показано, как получить встроенную **Общие** области **вывода** окна.  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Если добавить этот метод расширения, заданного в предыдущем разделе, при нажатии кнопки **вызова TestOutput** команды, вы увидите, что **выходные данные** окне отображаются слова **найти общие панель** в области.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Начало области построения окна вывода  
 В этом примере показано, как найти области построения и записи в файл. Так как в области построения не активирована по умолчанию, он активирует ее также.  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```
