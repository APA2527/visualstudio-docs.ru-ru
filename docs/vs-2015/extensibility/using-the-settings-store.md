---
title: С помощью параметров Store | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b6c2810a81ada06152faea06e86a27f7907a643
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430101"
---
# <a name="using-the-settings-store"></a>Использование хранилища параметров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Существует два типа хранилищ параметры:  
  
- Параметры конфигурации, которые являются только для чтения параметров Visual Studio и пакета VSPackage. Visual Studio объединяет параметры из всех известных .pkgdef файлов в это хранилище.  
  
- Параметры пользователя, для записи параметров, например те, которые отображаются на страницах в **параметры** диалоговое окно страниц свойств и некоторых других диалоговых окон. Расширения Visual Studio может использовать их для локального хранения небольших объемов данных.  
  
  В этом пошаговом руководстве показано, как считывать данные из хранилища параметров конфигурации. См. в разделе [записи Store параметры пользователя](../extensibility/writing-to-the-user-settings-store.md) объяснение способа записи в хранилище параметров пользователя.  
  
## <a name="creating-the-example-project"></a>Создание примера проекта  
 В этом разделе показано, как создать проект простое расширение с помощью команды меню для демонстрации.  
  
1. Все расширения Visual Studio начинается с проект развертывания VSIX, который будет содержать средств расширения. Создание [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проект VSIX с именем `SettingsStoreExtension`. Вы найдете шаблон проекта VSIX в **новый проект** диалоговое окно, в разделе **Visual C# / Extensibility**.  
  
2. Теперь Добавление пользовательской команды шаблона элемента с именем **SettingsStoreCommand**. В **Добавление нового элемента** диалоговое окно, перейдите к **Visual C# / Extensibility** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя командного файла для **SettingsStoreCommand.cs**. Дополнительные сведения о том, как создать настраиваемую команду см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>С помощью Store параметры конфигурации  
 В этом разделе показано, как обнаружить и отображать параметры конфигурации.  
  
1. В файле SettingsStorageCommand.cs, добавьте следующие операторы using:  
  
   ```  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.Settings;  
   using Microsoft.VisualStudio.Shell.Settings;  
   using System.Windows.Forms;  
   ```  
  
2. В `MenuItemCallback`, удалить тело метода и добавьте следующие строки получить хранилища параметров конфигурации:  
  
   ```  
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
   ```  
  
    <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> — Это управляемый вспомогательный класс через <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> службы.  
  
3. Теперь Узнайте, установлены ли средства Windows Phone. Код должен выглядеть следующим образом:  
  
   ```  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
       SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
       bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");  
       string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;  
       MessageBox.Show(message);  
   }  
   ```  
  
4. Тестирование кода. Выполните сборку решения и запустите отладку.  
  
5. В экспериментальном экземпляре на **средства** меню, щелкните **вызвать SettingsStoreCommand**.  
  
    Вы должны увидеть сообщение поле **средства для разработчиков Windows Phone:** следуют **True** или **False**.  
  
   Visual Studio будет хранить в хранилище параметров в системном реестре.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Использование редактора реестра для проверки параметров конфигурации  
  
1. Откройте Regedit.exe.  
  
2. Перейдите к HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.  
  
    > [!NOTE]
    > Убедитесь, что вы находитесь на ключ, который содержит \14.0Exp_Config\ и не \14.0_Config\\. Когда вы запускаете экспериментальном экземпляре Visual Studio, параметры конфигурации — в кусте реестра «14.0Exp_Config».  
  
3. Разверните узел \Installed Products\. Если сообщение на предыдущих шагах **установки по средств разработчика Microsoft Windows Phone: Значение true,**, \Installed Products\ должен содержать узел средства для разработчиков Windows Phone. Если сообщение является **разработчиков Microsoft Windows Phone средства установлены: False**, \Installed Products\ не должен содержать узел средства для разработчиков Windows Phone.
