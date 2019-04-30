---
title: Создание страницы параметров | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 63
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b5897f6c4463cc5a3c7928a722ed5a0a09e42b3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430582"
---
# <a name="creating-an-options-page"></a>Создание страницы параметров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве создается простой Сервис/Параметры страницы, использующей таблицу свойств для проверки и задать свойства.  
  
 Чтобы эти свойства, чтобы сохранить и восстановить их из файла параметров, выполните следующие действия и затем см. в разделе [Creating a Settings Category](../extensibility/creating-a-settings-category.md).  
  
 MPF предоставляет два класса для создания страниц параметров средств <xref:Microsoft.VisualStudio.Shell.Package> класс и <xref:Microsoft.VisualStudio.Shell.DialogPage> класса. Вы создадите предоставляют контейнер для этих страниц путем создания подклассов классу пакета VSPackage. Каждой страницы настроек инструментов создать путем наследования от класса DialogPage.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tools-options-grid-page"></a>Создание сетки страницы настроек инструментов  
 В этом разделе создайте простой Сервис-Параметры сетки свойств. При помощи данной сетки, чтобы отобразить и изменить значение свойства.  
  
#### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Чтобы создать проект VSIX и добавить VSPackage  
  
1. Все расширения Visual Studio начинается с проект развертывания VSIX, который будет содержать средств расширения. Создание [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проект VSIX с именем `MyToolsOptionsExtension`. Вы найдете шаблон проекта VSIX в **новый проект** диалоговое окно, в разделе **Visual C# / Extensibility**.  
  
2. Добавьте пакет VSPackage, добавив элемент шаблона пакета Visual Studio с именем `MyToolsOptionsPackage`. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**. В **диалоговое окно Add New Item**, перейдите в меню **элементы Visual C# / Extensibility** и выберите **пакета Visual Studio**. В **имя** в нижней части диалогового окна, измените имя файла для `MyToolsOptionsPackage.cs`. Дополнительные сведения о том, как создать пакет VSPackage, см. в разделе [создания расширения с помощью VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### <a name="to-create-the-tools-options-property-grid"></a>Создание сетки свойств Сервис-Параметры  
  
1. Откройте файл MyToolsOptionsPackage в редакторе кода.  
  
2. Добавьте следующий оператор using.  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3. Объявите класс OptionPageGrid и сделайте его производным от <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4. Применить <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> к классу VSPackage, чтобы присвоить классу параметры категории и имя страницы параметров для OptionPageGrid. Результат должен выглядеть следующим образом:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5. Добавить `OptionInteger` свойства `OptionPageGrid` класса.  
  
    - Применить <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> необходимо присвоить свойству категорию сетки свойств.  
  
    - Применить <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> необходимо присвоить имя свойству.  
  
    - Применить <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> необходимо присвоить свойству описание.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
  
        [Category("My Category")]  
        [DisplayName("My Integer Option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    > Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage> поддерживает свойства, имеющие соответствующие преобразователи типов или таблицы, структур или массивов, которые можно разделить на свойства, которые имеют соответствующие преобразователей. Список преобразователи типов, см. в разделе <xref:System.ComponentModel> пространства имен.  
  
6. Выполните сборку решения и запустите отладку.  
  
7. В экспериментальном экземпляре Visual Studio на **средства** меню **параметры**.  
  
     В левой области вы увидите **My Category**. (Параметры категории перечислены в алфавитном порядке, поэтому он должен отображаться о посередине вниз по списку.) Откройте **My Category** и нажмите кнопку **мою страницу сетки**. Сетка параметров в области справа. Свойство category — это **параметры**, и имя свойства является **Мои целочисленный параметр**. В описании свойства **моей целочисленный параметр**, отображается в нижней части области. Измените значение 256 исходное значение на другое. Нажмите кнопку **ОК**, а затем снова открыть **мою страницу сетки**. Вы увидите, что новое значение сохраняется.  
  
     Параметры страницы также доступна через панель быстрого запуска Visual Studio. Введите в окне быстрого запуска в правом верхнем углу интегрированной среды разработки **My Category** и вы увидите **My Category –> мою страницу сетки** в раскрывающемся списке.  
  
## <a name="creating-a-tools-options-custom-page"></a>Создание собственного средства параметры страницы  
 В этом разделе вы создадите страницы параметров средств с пользовательского интерфейса. Эта страница позволяет отображать и изменять значение свойства.  
  
1. Откройте файл MyToolsOptionsPackage в редакторе кода.  
  
2. Добавьте следующий оператор using.  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3. Добавить `OptionPageCustom` класса непосредственно перед `OptionPageGrid` класса. Нового производного класса от `DialogPage`.  
  
    ```csharp  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
4. Добавьте атрибут GUID. Добавьте свойство OptionString:  
  
    ```csharp  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
5. Применить секунды <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> к классу VSPackage. Этот атрибут присваивает класса категории параметров и имя страницы параметров.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    [ProvideOptionPage(typeof(OptionPageCustom),  
        "My Category", "My Custom Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
6. Добавьте новый **пользовательский элемент управления** с именем MyUserControl в проект.  
  
7. Добавить **TextBox** элемента управления в пользовательский элемент управления.  
  
     В **свойства** на панели инструментов щелкните **события** кнопку, а затем дважды щелкните **оставьте** событий. В коде MyUserControl.cs появляется новый обработчик событий.  
  
8. Добавьте открытое `OptionsPage` поле `Initialize` метод класса элемента управления и обновления, обработчик событий для задания параметра равным содержимое текстового поля:  
  
    ```csharp  
    public partial class MyUserControl : UserControl  
    {  
        public MyUserControl()  
        {  
            InitializeComponent();  
        }  
  
        internal OptionPageCustom optionsPage;  
  
        public void Initialize()  
        {  
            textBox1.Text = optionsPage.OptionString;  
        }  
  
        private void textBox1_Leave(object sender, EventArgs e)  
        {  
            optionsPage.OptionString = textBox1.Text;  
        }  
    }  
    ```  
  
     `optionsPage` Поле хранит ссылку на родительский `OptionPageCustom` экземпляра. `Initialize` Метод выводит `OptionString` в **TextBox**. Обработчик событий записывает текущее значение **TextBox** для `OptionString` когда фокус ввода находится оставляет **TextBox**.  
  
9. В файле кода пакет, добавьте переопределение для `OptionPageCustom.Window` свойство к классу OptionPageCustom, чтобы создать и инициализировать возврата экземпляра `MyUserControl`. Класс должен выглядеть следующим образом:  
  
    ```csharp  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
  
        protected override IWin32Window Window  
        {  
            get  
            {  
                MyUserControl page = new MyUserControl();  
                page.optionsPage = this;  
                page.Initialize();  
                return page;  
            }  
        }  
    }  
    ```  
  
10. Постройте и запустите проект.  
  
11. В экспериментальном экземпляре выберите **Сервис / Параметры**.  
  
12. Найти **Мои категории** и затем **настраиваемые страницы**.  
  
13. Измените значение свойства **OptionString**. Нажмите кнопку **ОК**, а затем снова открыть **Моя настраиваемая страница**. Вы увидите, что новое значение имеет постоянное.  
  
## <a name="accessing-options"></a>Доступ к параметрам  
 В этом разделе вы получите значение параметра, от VSPackage, на котором размещена соответствующая страница Сервис-Параметры. Ту же методику можно использовать для получения значения из любого общедоступного свойства.  
  
1. В файле кода пакет, добавьте открытое свойство с именем **OptionInteger** для **MyToolsOptionsPackage** класса.  
  
    ```  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     Этот код вызывает <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> создать или получить `OptionPageGrid` экземпляра. `OptionPageGrid` вызовы <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> для загрузки своих параметров, которые являются общедоступными свойствами.  
  
2. Теперь Добавление пользовательской команды шаблона элемента с именем **MyToolsOptionsCommand** для отображения значения. В **Добавление нового элемента** диалоговое окно, перейдите к **Visual C# / Extensibility** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя командного файла для **MyToolsOptionsCommand.cs**.  
  
3. В файле MyToolsOptionsCommand, замените текст команды `ShowMessageBox` следующим кодом:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4. Выполните сборку решения и запустите отладку.  
  
5. В экспериментальном экземпляре на **средства** меню, щелкните **вызвать MyToolsOptionsCommand**.  
  
     Окно сообщения отображает текущее значение `OptionInteger`.  
  
## <a name="see-also"></a>См. также  
 [Параметры и страницы параметров](../extensibility/internals/options-and-options-pages.md)
