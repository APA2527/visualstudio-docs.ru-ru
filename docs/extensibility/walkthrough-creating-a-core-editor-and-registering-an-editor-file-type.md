---
title: Создание базового редактора и регистрация файла тип редактора | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4aac1298c13cb931eba889e6323faff9b1640f8b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411036"
---
# <a name="walkthrough-create-a-core-editor-and-registering-an-editor-file-type"></a>Пошаговое руководство. Создание базового редактора и регистрации файла тип редактора
В этом пошаговом руководстве показано, как создать пакет VSPackage, который запускает [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] базового редактора при создании файла с *.myext* загружается расширение имени файла.

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Расположения для шаблона проекта пакета Visual Studio
 Шаблон проекта пакета Visual Studio можно найти в трех разных местах диалогового окна **Создание проекта** .

1. В разделе **расширения Visual Basic**. Язык проекта по умолчанию — Visual Basic.

2. В разделе **расширения Visual C#**. Язык проекта по умолчанию — C#.

3. В разделе **расширения других типов проектов**. Язык проекта по умолчанию — C++.

### <a name="to-create-the-vspackage"></a>Чтобы создать VSPackage

- Запуск [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и создайте [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] VSPackage с именем `MyPackage`, как описано в [Пошаговое руководство: Создание команды меню VSPackage](https://msdn.microsoft.com/library/d699c149-5d1e-47ff-94c7-e1222af02c32).

### <a name="to-add-the-editor-factory"></a>Чтобы добавить фабрики редактора

1. Щелкните правой кнопкой мыши **MyPackage** проект, выберите пункт **добавить**, а затем нажмите кнопку **класс**.

2. В **Добавление нового элемента** диалогового окна поле, убедитесь, что **класс** выбран шаблон, тип `EditorFactory.cs` имя, а затем нажмите кнопку **добавить** Добавление класса в проект.

    *EditorFactory.cs* должно автоматически открыть файл.

3. Ссылки на следующие сборки из кода.

   ```vb
   Imports System.Runtime.InteropServices
   Imports Microsoft.VisualStudio
   Imports Microsoft.VisualStudio.Shell
   Imports Microsoft.VisualStudio.Shell.Interop
   Imports Microsoft.VisualStudio.OLE.Interop
   Imports Microsoft.VisualStudio.TextManager.Interop
   Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider
   ```

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio;
   using Microsoft.VisualStudio.Shell;
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio.OLE.Interop;
   using Microsoft.VisualStudio.TextManager.Interop;
   using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;

   ```

4. Добавьте идентификатор GUID, `EditorFactory` класса путем добавления `Guid` атрибут непосредственно перед объявлением класса.

    Новый идентификатор GUID можно создать с помощью *guidgen.exe* программирования на [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или командной строке, щелкнув **создать GUID** на **средства** меню. GUID, используемый здесь указано только для примера; не используйте его в проект.

   ```vb
   <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _
   ```

   ```csharp
   [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]
   ```

5. В определении класса добавьте две закрытых переменных родительского пакета и поставщика услуг.

   ```vb
   Class EditorFactory
       Private parentPackage As Package
       Private serviceProvider As IOleServiceProvider
   ```

   ```csharp
   class EditorFactory
   {
       private Package parentPackage;
       private IOleServiceProvider serviceProvider;
   }

   ```

6. Добавьте конструктор открытый класс, который принимает один параметр типа <xref:Microsoft.VisualStudio.Shell.Package>:

   ```vb
   Public Sub New(ByVal parentPackage As Package)
       Me.parentPackage = parentPackage
   End Sub
   ```

   ```csharp
   public EditorFactory(Package parentPackage)
   {
       this.parentPackage = parentPackage;
   }
   ```

7. Изменить `EditorFactory` объявление для наследования от класса <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейс.

   ```vb
   Class EditorFactory Implements IVsEditorFacto
   ```

   ```csharp
   class EditorFactory : IVsEditorFactory

   ```

8. Щелкните правой кнопкой мыши <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>, нажмите кнопку **реализовать интерфейс**, а затем нажмите кнопку **реализовать интерфейс явно**.

    На этом шаге добавляется четыре метода, которые должны быть реализованы в <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейс.

9. Замените содержимое метода `IVsEditorFactory.Close` следующим кодом.

    ```vb
    Return VSConstants.S_OK
    ```

    ```csharp
    return VSConstants.S_OK;
    ```

10. Замените содержимое файла `IVsEditorFactory.SetSite` следующим кодом.

    ```vb
    Me.serviceProvider = psp
    Return VSConstants.S_OK
    ```

    ```csharp
    this.serviceProvider = psp;
    return VSConstants.S_OK;
    ```

11. Замените содержимое метода `IVsEditorFactory.MapLogicalView` следующим кодом.

    ```vb
    Dim retval As Integer = VSConstants.E_NOTIMPL
    pbstrPhysicalView = Nothing ' We support only one view.
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then
        retval = VSConstants.S_OK
    End If
    Return retval
    ```

    ```csharp
    int retval = VSConstants.E_NOTIMPL;
    pbstrPhysicalView = null;   // We support only one view.
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))
    {
        retval = VSConstants.S_OK;
    }
    return retval;
    ```

12. Замените содержимое метода `IVsEditorFactory.CreateEditorInstance` следующим кодом.

    ```vb
    Dim retval As Integer = VSConstants.E_FAIL

    ' Initialize these to empty to start with
    ppunkDocView = IntPtr.Zero
    ppunkDocData = IntPtr.Zero
    pbstrEditorCaption = ""
    pguidCmdUI = Guid.Empty
    pgrfCDW = 0

    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _
    VSConstants.CEF_SILENT)) = 0 Then
        Throw New ArgumentException("Only Open or Silent is valid")
    End If
    If punkDocDataExisting <> IntPtr.Zero Then
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA
    End If

    ' Instantiate a text buffer of type VsTextBuffer.
    ' Note: we only need an IUnknown (object) interface for
    ' this invocation.
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown
    Dim pTextBuffer As Object = pTextBuffer = _
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _
    GetType(Object))

    If Not pTextBuffer Is Nothing Then
        ' "Site" the text buffer with the service provider we were
        ' provided.
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _
        IObjectWithSite)
        If Not textBufferSite Is Nothing Then
            textBufferSite.SetSite(Me.serviceProvider)
        End If

        ' Instantiate a code window of type IVsCodeWindow.
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID
        Dim pCodeWindow As IVsCodeWindow = _
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)
        If Not pCodeWindow Is Nothing Then
            ' Give the text buffer to the code window.
            ' We are giving up ownership of the text buffer!
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))

            ' Now tell the caller about all this new stuff
            ' that has been created.
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)

            ' Specify the command UI to use so keypresses are
            ' automatically dealt with.
            pguidCmdUI = VSConstants.GUID_TextEditorFactory

            ' This caption is appended to the filename and
            ' lets us know our invocation of the core editor
            ' is up and running.
            pbstrEditorCaption = " [MyPackage]"

            retval = VSConstants.S_OK
        End If
    End If
    Return retval
    ```

    ```csharp
    int retval = VSConstants.E_FAIL;

    // Initialize these to empty to start with
    ppunkDocView       = IntPtr.Zero;
    ppunkDocData       = IntPtr.Zero;
    pbstrEditorCaption = "";
    pguidCmdUI         = Guid.Empty; 
    pgrfCDW            = 0;

    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |
          VSConstants.CEF_SILENT)) == 0)
    { 
        throw new ArgumentException("Only Open or Silent is valid");
    }
    if (punkDocDataExisting != IntPtr.Zero)
    {
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;
    }

    // Instantiate a text buffer of type VsTextBuffer.
    // Note: we only need an IUnknown (object) interface for 
    // this invocation.
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(
          ref clsidTextBuffer,
          ref iidTextBuffer,
          typeof(object));

    if (pTextBuffer != null)
    {
        // "Site" the text buffer with the service provider we were
        // provided.
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;
        if (textBufferSite != null)
        {
            textBufferSite.SetSite(this.serviceProvider);
        }

        // Instantiate a code window of type IVsCodeWindow.
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;
        IVsCodeWindow pCodeWindow =
        (IVsCodeWindow)this.parentPackage.CreateInstance( 
              ref clsidCodeWindow,
              ref iidCodeWindow,
              typeof(IVsCodeWindow));
        if (pCodeWindow != null)
        {
            // Give the text buffer to the code window.
            // We are giving up ownership of the text buffer!
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);

            // Now tell the caller about all this new stuff 
            // that has been created.
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);

            // Specify the command UI to use so keypresses are 
            // automatically dealt with.
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;

            // This caption is appended to the filename and
            // lets us know our invocation of the core editor 
            // is up and running.
            pbstrEditorCaption = " [MyPackage]";

            retval = VSConstants.S_OK;
        } 
    } 
    return retval; 
    ```

13. Скомпилируйте проект и убедитесь, что ошибок нет.

### <a name="to-register-the-editor-factory"></a>Регистрация фабрики редактора

1. В **обозревателе решений**, дважды щелкните **Resources.resx** файл, чтобы открыть его в таблице строк, в котором операция **строка1** выбранного.

2. Измените имя идентификатора, `IDS_EDITORNAME` и текст, который **MyPackage редактора.** Эта строка отображается как имя редактора.

3. Откройте **VSPackage.resx** файл, добавьте новую строку, задайте имя **101**и задайте значение `IDS_EDITORNAME`. Этот шаг предоставляет пакет с Идентификатором ресурса для доступа к строке, которую вы создали.

   > [!NOTE]
   > Если **VSPackage.resx** файл содержит другой строкой, которую `name` атрибут **101**, заменить другой уникальное числовое значение, здесь и далее.

4. В **обозревателе решений**откройте **MyPackagePackage.cs** файла.

    Этот файл является файлом главного пакета.

5. Добавьте следующие атрибуты пользователя непосредственно перед `Guid` атрибута.

   ```vb
   <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _
   <ProvideEditorExtensionAttribute(GetType(EditorFactory), _
         ".myext", 32, NameResourceID:=101 )> _
   ```

   ```csharp
   [ProvideEditorFactory(typeof(EditorFactory), 101)]
   [ProvideEditorExtension(typeof(EditorFactory),
         ".myext", 32, NameResourceID = 101)]
   ```

    <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> Атрибута связывает *.myext* расширением с вашей фабрикой редактора, чтобы в любое время в файл с расширение загружается, вызывается фабрикой редактора.

6. Добавьте частную переменную для `MyPackage` класса просто перед конструктором и присвойте ей тип `EditorFactory`.

   ```vb
   Private editorFactory As EditorFactory
   ```

   ```csharp
   private EditorFactory editorFactory;
   ```

7. Найти `Initialize` метод (возможно открыть `Package Members` скрытой области) и добавьте следующий код после вызова `base.Initialize()`.

   ```vb
   'Create our editor factory and register it.
   Me.editorFactory = New EditorFactory(Me)
   MyBase.RegisterEditorFactory(Me.editorFactory)
   ```

   ```csharp
   // Create our editor factory and register it.
   this.editorFactory = new EditorFactory(this);
   base.RegisterEditorFactory(this.editorFactory);

   ```

8. Скомпилируйте программу и убедитесь в отсутствии ошибок.

    Этот шаг регистрирует фабрику редактора в экспериментальном кусте реестра для [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. При появлении в Переопределите *resource.h* щелкните **ОК**.

9. Создание образца файла с именем *TextFile1.myext*.

10. Нажмите клавишу **F5** чтобы открыть экспериментальный экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

11. В экспериментальном экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]на **файл** последовательно выберите пункты **откройте** и нажмите кнопку **файл**.

12. Найти **TextFile1.myext** и нажмите кнопку **откройте**.

     Файл должен загружаться.

## <a name="robust-programming"></a>Отказоустойчивость
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Базовый редактор обрабатывает широкий диапазон типов текстовых файлов и тесно сотрудничает с языковые службы, обеспечивая широкий набор функций, таких как выделение синтаксиса, парные фигурные скобки и завершение слов IntelliSense и автозавершение элементов перечислены. Если вы работаете с файлами на основе текста, можно использовать базовый редактор вместе с пользовательский языковой службы, которая поддерживает ваши определенные типы файлов.

 VSPackage может вызывать [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] базовым редактором, указав фабрику редактора. Этой фабрикой редактора используется каждый раз, когда загружается файл, который связан с ним. Если файл является частью проекта, базовый редактор автоматически вызывается, если не переопределено VSPackage. Тем не менее если файл загружается за пределами проекта, базовым редактором должны явно вызываться с VSPackage.

 Дополнительные сведения о редакторе см. в разделе [внутри базовым редактором](../extensibility/inside-the-core-editor.md).

## <a name="see-also"></a>См. также
- [В редакторе](../extensibility/inside-the-core-editor.md)
- [Создать экземпляр базового редактора с помощью предыдущих версий API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)