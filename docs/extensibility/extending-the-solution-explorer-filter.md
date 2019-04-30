---
title: Расширение фильтра обозревателя решений | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef9439d9cebfa8b80b214e52d077ab1f770d4750
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912130"
---
# <a name="extend-the-solution-explorer-filter"></a>Расширение фильтра обозревателя решений
Вы можете расширить **обозревателе решений** фильтрации функциональные возможности для отображения или скрытия разные файлы. Например, можно создать фильтр, показывающий только файлов C# класса фабрики в **обозревателе решений**, как показано в этом пошаговом руководстве.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-package-project"></a>Создайте проект пакета Visual Studio

1. Создайте проект VSIX с именем `FileFilter`. Добавление пользовательской команды шаблона элемента с именем **FileFilter**. Дополнительные сведения см. в разделе [создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Добавьте ссылку на `System.ComponentModel.Composition` и `Microsoft.VisualStudio.Utilities`.

3. Команда меню отображаются на **обозревателе решений** панели инструментов. Откройте *FileFilterPackage.vsct* файла.

4. Изменение `<Button>` блок следующим:

    ```xml
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>FileNameFilter</ButtonText>
        </Strings>
    </Button>
    ```

### <a name="update-the-manifest-file"></a>Обновление файла манифеста

1. В *source.extension.vsixmanifest* добавьте ресурс-контейнер, — это компонент MEF.

2. На **активы** вкладке, выберите **New** кнопки.

3. В **тип** переключатель **Microsoft.VisualStudio.MefComponent**.

4. В **источника** переключатель **проект в текущем решении**.

5. В **проекта** переключатель **FileFilter**, а затем выберите **ОК** кнопки.

### <a name="add-the-filter-code"></a>Добавьте код фильтра

1. Добавить некоторые идентификаторы GUID для *FileFilterPackageGuids.cs* файла:

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. Добавьте файл класса с именем проекта FileFilter *FileNameFilter.cs*.

3. Замените пустое пространство имен и пустой класс приведенный ниже код.

     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` Метод принимает коллекцию, содержащую корневой папке решения (`rootItems`) и возвращает коллекцию элементов, включаемых в фильтр.

     `ShouldIncludeInFilter` Метод фильтрует элементы в **обозревателе решений** на основе при условии, что указываемые иерархии.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Text.RegularExpressions;
    using System.Threading.Tasks;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;

    namespace FileFilter
    {
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider
        {
            SVsServiceProvider svcProvider;
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

            // Constructor required for MEF composition
            [ImportingConstructor]
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)
            {
                this.svcProvider = serviceProvider;
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;
            }

            // Returns an instance of Create filter class.
            protected override HierarchyTreeFilter CreateFilter()
            {
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);
            }

            // Regex pattern for CSharp factory classes
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";

            // Implementation of file filtering
            private sealed class FileNameFilter : HierarchyTreeFilter
            {
                private readonly Regex regexp;
                private readonly IServiceProvider svcProvider;
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

                public FileNameFilter(
                    IServiceProvider serviceProvider,
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,
                    string fileNamePattern)
                {
                    this.svcProvider = serviceProvider;
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);
                }

                // Gets the items to be included from this filter provider.
                // rootItems is a collection that contains the root of your solution
                // Returns a collection of items to be included as part of the filter
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)
                {
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(
                                        root.HierarchyIdentity.NestedHierarchy,
                                        CancellationToken);

                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(
                        sourceItems,
                        ShouldIncludeInFilter,
                        CancellationToken);
                    return includedItems;
                }

                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)
                {
                    if (hierarchyItem == null)
                    {
                        return false;
                    }
                    return this.regexp.IsMatch(hierarchyItem.Text);
                }
            }
        }
    }

    ```

4. В *FileFilter.cs*, удалите размещения команд и кода из конструктора FileFilter обработки. Результат должен выглядеть следующим образом:

    ```csharp
    private FileFilter(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;
    }
    ```

     Удалить `ShowMessageBox()` также метод.

5. В *FileFilterPackage.cs*, замените код в `Initialize()` следующим кодом:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Тестирование кода

1. Постройте и запустите проект. Откроется второй экземпляр Visual Studio. Это называется экспериментальным.

2. В экспериментальном экземпляре Visual Studio откройте проект C#.

3. Найдите кнопку вы добавили в **обозревателе решений** панели инструментов. Она должна быть Четвертая кнопка слева.

4. При нажатии кнопки, необходимо отфильтровать все файлы и вы увидите **все элементы были отфильтрованы из представления.** в **обозревателе решений**.