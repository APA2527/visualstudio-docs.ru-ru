---
title: Создание расширения с помощью команды меню | Документация Майкрософт
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb18792e2d0d357bb131af6c12e97425cd72fd05
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345371"
---
# <a name="create-an-extension-with-a-menu-command"></a>Создание расширения с помощью команды меню

В этом пошаговом руководстве показано, как создать расширение с помощью команды меню, которое запускает приложение Блокнот.

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-command"></a>Создание команды меню

1. Создайте проект VSIX с именем **FirstMenuCommand**. Вы найдете шаблон проекта VSIX в **новый проект** диалоговое окно, выполняя поиск «vsix».

2. При открытии проекта, Добавление пользовательской команды шаблона элемента с именем **FirstCommand**. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить** > **новый элемент**. В **Добавление нового элемента** диалоговое окно, перейдите к **Visual C#**  > **расширяемости** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя командного файла для *FirstCommand.cs*.

3. Выполните сборку решения и запустите отладку.

    Откроется экспериментальный экземпляр Visual Studio. Дополнительные сведения о экспериментальный экземпляр, см. в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. В экспериментальном экземпляре откройте **средства** > **расширения и обновления** окна. Вы должны увидеть **FirstMenuCommand** здесь расширения. (Если вы откроете **расширения и обновления** в свой рабочий экземпляр Visual Studio, вы не увидите **FirstMenuCommand**).

::: moniker-end

::: moniker range=">=vs-2019"

4. В экспериментальном экземпляре откройте **расширения** > **Управление расширениями** окна. Вы должны увидеть **FirstMenuCommand** здесь расширения. (Если вы откроете **Управление расширениями** в свой рабочий экземпляр Visual Studio, вы не увидите **FirstMenuCommand**).

::: moniker-end

Теперь перейдите к **средства** меню в экспериментальном экземпляре. Вы должны увидеть **вызова FirstCommand** команды. На этом этапе появится окно сообщения с текстом **FirstCommandPackage внутри FirstMenuCommand.FirstCommand.MenuItemCallback()** . Мы рассмотрим фактически запустить Блокнот этой команды в следующем разделе.

## <a name="change-the-menu-command-handler"></a>Изменить обработчик команд меню

Теперь давайте обновим обработчик команды для запуска блокнота.

1. Остановить отладку и вернитесь в рабочий экземпляр Visual Studio. Откройте *FirstCommand.cs* файл и добавьте следующий оператор using:

    ```csharp
    using System.Diagnostics;
    ```

2. Найдите закрытый конструктор FirstCommand. Это, когда команда, привязанную службу команд, и обработчик команды определяется. Измените имя обработчика команды StartNotepad, следующим образом:

    ```csharp
    private FirstCommand(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        CommandID menuCommandID = new CommandID(CommandSet, CommandId);
        // Change to StartNotepad handler.
        MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

3. Удалить `MenuItemCallback` метод и добавьте `StartNotepad` метод, который будет просто запустите Блокнот:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Теперь попробуйте все в деле. При запуске отладки проекта и нажмите кнопку **средства** > **вызова FirstCommand**, вы увидите экземпляр блокнота отобразились.

    Можно использовать экземпляр <xref:System.Diagnostics.Process> класса для запуска любого исполняемого файла, а не только «Блокнот». Оцените его с `calc.exe`, например.

## <a name="clean-up-the-experimental-environment"></a>Очистить экспериментальной среде

Если вы разрабатываете несколько расширений, просто изучаете результаты с разными версиями кода расширения, в экспериментальной среде могут перестать работать так, ее нужно. В этом случае следует запускать скрипт сброса. Он называется **Сброс экспериментального экземпляра Visual Studio**, и он поставляется как часть Visual Studio SDK. Этот сценарий удаляет все ссылки на расширения из экспериментальной среды, вы можете начать с нуля.

Вы можете получить в этот сценарий в одном из двух способов:

1. На рабочем столе найти **Сброс экспериментального экземпляра Visual Studio**.

2. Выполните следующую команду в командной строке:

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Развертывание модуля

Теперь, когда у вас есть расширение средства запуска нужным образом, пришло время подумать о совместной работы с коллегами и друзьями. Это простой, до тех пор, пока они установлена среда Visual Studio 2015. Все, что необходимо сделать отправить им *.vsix* созданный файл. (Не забудьте скомпилировать его в режиме выпуска).

Можно найти *.vsix* файл для этого расширения в *FirstMenuCommand* каталог bin. В частности при условии, что выполнена сборка конфигурации выпуска, он будет иметь:

*\<каталог кода > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix*

Чтобы установить расширение, ваш друг необходимо закрыть все открытые экземпляры Visual Studio, а затем дважды щелкните *.vsix* файл, который можно открыть **установщик VSIX**. Файлы копируются на *%LocalAppData%\Microsoft\VisualStudio\<версии > \Extensions* каталога.

Когда ваш друг можно открыть Visual Studio еще раз, смогут найти расширения FirstMenuCommand в **средства** > **расширения и обновления**. Они могут перейти **расширения и обновления** удаление или отключение расширения, слишком.

## <a name="next-steps"></a>Следующие шаги

В этом пошаговом руководстве были показаны только небольшая часть действий, выполняемых с расширением Visual Studio. Ниже приведен краткий список прочего (довольно просто), которые можно выполнить с помощью расширений Visual Studio:

1. Можно выполнять другие действия с помощью команды простого меню:

   1. Добавьте собственный значок: [Добавление значков для команды меню](../extensibility/adding-icons-to-menu-commands.md)

   2. Измените текст команды меню: [Изменить текст команды меню](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Добавьте команду контекстного меню: [Привязка сочетания клавиш к пунктам меню](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Добавьте различные команды, меню и панелей инструментов: [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)

3. Добавление окна инструментов и расширения встроенных окон инструментов Visual Studio: [Расширение и настройка окон инструментов](../extensibility/extending-and-customizing-tool-windows.md)

4. Добавьте существующие редакторы кода IntelliSense, предложения кода и другие возможности: [Расширение редактора и языковой службы](../extensibility/extending-the-editor-and-language-services.md)

5. Добавьте параметры и свойства страниц и пользовательских параметров расширения: [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md) и [расширить пользовательские настройки и параметры](../extensibility/extending-user-settings-and-options.md)

   Другие виды расширений требуют немного больше работы, таких как создание нового типа проекта ([расширения проектов](../extensibility/extending-projects.md)), создания нового типа редактора ([создание специализированных редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)), или реализация вашей расширения в изолированной оболочки. [Visual Studio изолированной оболочки](/visualstudio/extensibility/shell/visual-studio-isolated-shell)
