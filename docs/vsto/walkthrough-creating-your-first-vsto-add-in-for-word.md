---
title: Пошаговое руководство. Создание первой надстройки VSTO для Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Word [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ed5c5e5b03ce7ee0ffbd361b896f288f6b93a806
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438505"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-word"></a>Пошаговое руководство. Создание первой надстройки VSTO для Word
  В этом вводном пошаговом руководстве показано, как создать надстройку VSTO для Microsoft Office Word. Функции, создаваемые в таком решении, доступны для самого приложения независимо от того, какие документы открыты.

 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

 В данном пошаговом руководстве рассмотрены следующие задачи:

- Создание проекта надстройки VSTO для Word

- Написание кода, который использует объектную модель Word для добавления текста в документ при его сохранении.

- Построение и запуск проекта для тестирования.

- Удаление завершенного проекта для прекращения автоматического запуска надстройки VSTO на компьютере разработчика.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Создание проекта

### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>Создание нового проекта надстройки VSTO для Word в Visual Studio

1. Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

3. В области шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем узел **Office/SharePoint**.

4. В развернутом узле **Office/SharePoint** выберите узел **Надстройки Office** .

5. В списке шаблонов проектов выберите проект надстройки VSTO для Word.

6. В **имя** введите **FirstWordAddIn**.

7. Нажмите кнопку **ОК**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Создает **FirstWordAddIn** проект и открывает файл кода ThisAddIn в редакторе.

## <a name="write-code-to-add-text-to-the-saved-document"></a>Написать код для добавления текста в сохраненный документ
 Затем добавьте код в файл ThisAddIn. Новый код использует объектную модель Word для добавления стандартного текста в каждый сохраненный документ. По умолчанию файл кода ThisAddIn содержит следующий созданный код:

- Частичное определение класса `ThisAddIn` . Этот класс предоставляет точку входа для кода и обеспечивает доступ к объектной модели Word. Дополнительные сведения см. в разделе [программы VSTO Add-ins](../vsto/programming-vsto-add-ins.md). Остальная часть класса `ThisAddIn` определяется в скрытом файле кода, изменять который не следует.

- Обработчики событий `ThisAddIn_Startup` и `ThisAddIn_Shutdown` . Эти обработчики событий вызываются, когда Excel загружает и выгружает надстройку VSTO. Их можно использовать для инициализации надстройки VSTO в процессе ее загрузки, а также для освобождения ресурсов, используемых вашей надстройкой VSTO при ее выгрузке. Дополнительные сведения см. в разделе [события в проектах Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>Добавление абзаца текста в сохраненный документ

1. В файл кода ThisAddIn добавьте в класс `ThisAddIn` указанный ниже код. Новый код определяет обработчик событий для события <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>, которое возникает при сохранении документа.

    Когда пользователь сохраняет документ, обработчик событий добавляет новый текст в начало документа.

    [!code-vb[Trin_WordAddInTutorial#1](../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb#1)]
    [!code-csharp[Trin_WordAddInTutorial#1](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#1)]

   > [!NOTE]
   > Этот код использует значение индекса 1 для доступа к первому абзацу в коллекции <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A>. Хотя Visual Basic и Visual C# используют массивы, которые начинаются с 0, нижней границей массива для большинства коллекций в объектной модели Word является 1. Дополнительные сведения см. в разделе [написания кода в решениях Office](../vsto/writing-code-in-office-solutions.md).

2. Если используется C#, добавьте в обработчик событий `ThisAddIn_Startup` указанный ниже код. Он используется для подключения обработчика событий `Application_DocumentBeforeSave` к событию <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> .

    [!code-csharp[Trin_WordAddInTutorial#2](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#2)]

   Для изменения документа при его сохранении в приведенных выше примерах кода используются следующие объекты.

- Поле `Application` класса `ThisAddIn` . Поле `Application` возвращает объект <xref:Microsoft.Office.Interop.Word.Application>, который представляет текущий экземпляр Word.

- Параметр `Doc` обработчика событий для события <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> . Параметр `Doc` является объектом <xref:Microsoft.Office.Interop.Word.Document>, который представляет сохраненный документ. Дополнительные сведения см. в разделе [обзор объектной модели Word](../vsto/word-object-model-overview.md).

## <a name="test-the-project"></a>Тестирование проекта

### <a name="to-test-the-project"></a>Тестирование проекта

1. Нажмите клавишу **F5** для построения и запуска проекта.

     При построении проекта код компилируется в сборку, которая включается в выходную папку сборки для проекта. Visual Studio также создает ряд записей реестра, которые позволяют Excel обнаружить и загрузить надстройку VSTO, и настраивает параметры безопасности на компьютере разработчика, разрешая запуск надстройки VSTO. Дополнительные сведения см. в разделе [решений Office построения](../vsto/building-office-solutions.md).

2. В Word сохраните активный документ.

3. Убедитесь, что в документ добавлен следующий текст.

     **Этот текст добавляется с помощью кода.**

4. Закройте Word.

## <a name="clean-up-the-project"></a>Очистка проекта
 Завершив разработку проекта, удалите с компьютера сборку надстройки VSTO, записи реестра и параметры безопасности. В противном случае надстройка VSTO будет запускаться при каждом открытии программы Word на компьютере разработчика.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Очистка завершенного проекта на компьютере разработчика

1. В Visual Studio в меню **Построение** выберите пункт **Очистить решение**.

## <a name="next-steps"></a>Следующие шаги
 Теперь, когда вы создали базовую надстройку VSTO для Word, ознакомьтесь с более подробными сведениями о разработке надстроек VSTO в следующих разделах.

- Общие задачи программирования, которые можно выполнять в надстройках VSTO: [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md).

- Программирование задачи, характерные для надстроек VSTO для Word: [Решения Word](../vsto/word-solutions.md).

- С помощью объектной модели Word: [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md).

- Настройка пользовательского интерфейса Word, например, путем добавления настраиваемой вкладки на ленту или создания собственной настраиваемой области задач: [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).

- Построение и отладка надстроек VSTO для Word: [Создание решений Office](../vsto/building-office-solutions.md).

- Развертывание надстроек VSTO для Word: [Развертывание решения Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>См. также
- [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Решения Word](../vsto/word-solutions.md)
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Обзор объектной модели Word](../vsto/word-object-model-overview.md)
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Создание решений Office](../vsto/building-office-solutions.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
- [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)
