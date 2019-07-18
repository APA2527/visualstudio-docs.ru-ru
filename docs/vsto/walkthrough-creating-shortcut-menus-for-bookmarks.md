---
title: Пошаговое руководство. Создать контекстное меню для закладок
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9b4b412d2e9456142c1be1af388e2803634d15c0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438544"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>Пошаговое руководство. Создать контекстное меню для закладок
  В этом пошаговом руководстве показано, как создать контекстное меню для <xref:Microsoft.Office.Tools.Word.Bookmark> элементов управления в настройке уровня документа для Word. Когда пользователь щелкает правой кнопкой мыши текст в закладку, контекстное меню отображается и параметры для форматирования текста.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 В данном пошаговом руководстве рассмотрены следующие задачи:

- [Создание проекта](#BKMK_CreateProject).

- [Добавление текста и закладок в документе](#BKMK_addtextandbookmarks).

- [Добавление команд в контекстное меню](#BKMK_AddCmndsShortMenu).

- [Форматирование текста в закладке](#BKMK_formattextbkmk).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="BKMK_CreateProject"></a> Создание проекта
 Первым шагом является создание проекта документа Word в Visual Studio.

### <a name="to-create-a-new-project"></a>Создание нового проекта

- Создайте проект документа Word с именем **Мое контекстное меню закладок**. В мастере выберите **создания документа**. Дополнительные сведения см. в разделе [Как Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio открывает новый документ Word в конструкторе и добавляет **Мое контекстное меню закладок** проект **обозревателе решений**.

## <a name="BKMK_addtextandbookmarks"></a> Добавление текста и закладок в документ
 Добавьте в документ текст, а затем добавьте двумя перекрывающимися закладками.

### <a name="to-add-text-to-your-document"></a>Для добавления текста в документ

- В документе, который отображается в конструкторе проекта введите следующий текст.

     **Ниже приведен пример создания контекстного меню при щелчке правой кнопкой мыши текст в закладку.**

### <a name="to-add-a-bookmark-control-to-your-document"></a>Добавление элемента управления Bookmark в документ

1. В **элементов**, из **элементы управления Word** вкладке, перетащите <xref:Microsoft.Office.Tools.Word.Bookmark> элемента управления в документ.

    **Добавьте элемент управления Bookmark** откроется диалоговое окно.

2. Выделите слова «Создание контекстного меню при щелчке правой кнопкой мыши текст», а затем нажмите кнопку **ОК**.

    `bookmark1` добавляется к документу.

3. Добавьте еще один <xref:Microsoft.Office.Tools.Word.Bookmark> управления слова «щелкните правой кнопкой мыши текст в закладку».

    `bookmark2` добавляется к документу.

   > [!NOTE]
   > Слова «щелкните правой кнопкой мыши текст» находятся в `bookmark1` и `bookmark2`.

   При добавлении закладки в документ во время разработки, <xref:Microsoft.Office.Tools.Word.Bookmark> создается элемент управления. Можно запрограммировать несколько событий закладки. Можно написать код <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> события закладки, чтобы при щелчке правой кнопкой мыши на текст в закладку, появится контекстное меню.

## <a name="BKMK_AddCmndsShortMenu"></a> Добавление команд в контекстное меню
 Добавление кнопок в контекстное меню, которое появляется при щелчке правой кнопкой мыши документ.

### <a name="to-add-commands-to-a-shortcut-menu"></a>Чтобы добавить команды в контекстное меню

1. Добавить **Ribbon XML** элемента в проект. Дополнительные сведения см. в разделе [Как Приступая к настройке ленты](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. В **обозревателе решений**выберите **ThisDocument.cs** или **ThisDocument.vb**.

3. В строке меню выберите **Вид** > **Код**.

     **ThisDocument** в редакторе кода откроется файл класса.

4. Добавьте следующий код, чтобы **ThisDocument** класса. Этот код переопределяет метод CreateRibbonExtensibilityObject и возвращает класс XML ленты в приложение Office.

     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]

5. В **обозревателе решений**выберите XML-файл ленты. По умолчанию XML-файл ленты называется Ribbon1.xml.

6. В строке меню выберите **Вид** > **Код**.

     XML-файл ленты открывается в редакторе кода.

7. В редакторе кода замените содержимое файла XML-код ленты следующим кодом.

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="BoldButton" label="Bold" onAction="ButtonClick"
               getVisible="GetVisible" />
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"
              getVisible="GetVisible"/>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

     Этот код добавляет две кнопки в контекстное меню, которое появляется при щелчке правой кнопкой мыши документ.

8. В **обозревателе решений**, щелкните правой кнопкой мыши `ThisDocument`, а затем нажмите кнопку **Просмотр кода**.

9. Объявите следующие переменные и переменные закладки на уровне класса.

     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]

10. В **обозревателе решений**, выберите файл кода ленты. По умолчанию файл кода ленты называется **Ribbon1.cs** или **Ribbon1.vb**.

11. В строке меню выберите **Вид** > **Код**.

     Файл кода ленты открывается в редакторе кода.

12. В файле кода ленты добавьте следующий метод. Это метод обратного вызова для обеих кнопок, добавленных в контекстное меню документа. Этот метод определяет, отображается ли эти кнопки в контекстном меню. Эмуляция полужирного курсивного кнопки отображались только в том случае, если щелкнуть правой кнопкой мыши текста в закладке.

     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]

## <a name="BKMK_formattextbkmk"></a> Форматирование текста в закладке

### <a name="to-format-the-text-in-the-bookmark"></a>Для форматирования текста в закладке

1. В файле кода ленты добавьте `ButtonClick` обработчик событий, чтобы применить форматирование к закладке.

     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]

2. **Обозреватель решений**выберите **ThisDocument.cs** или **ThisDocument.vb**.

3. В строке меню выберите **Вид** > **Код**.

     **ThisDocument** в редакторе кода откроется файл класса.

4. Добавьте следующий код, чтобы **ThisDocument** класса.

     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]

    > [!NOTE]
    > Необходимо написать код для обработки перекрывающимися закладками. Если этого не сделать, по умолчанию, код будет вызываться для всех закладок в выделении.

5. В C# необходимо добавить обработчики событий для элементов управления bookmark в <xref:Microsoft.Office.Tools.Word.Document.Startup> событий. Сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]

## <a name="test-the-application"></a>Тестирование приложения
 Проверьте документ и убедитесь, что элементы меню полужирного шрифта и курсива отображаются в контекстном меню при щелчке правой кнопкой мыши текст в закладку и что текст имеет правильный формат.

### <a name="to-test-your-document"></a>Проверка документа

1. Нажмите клавишу **F5** для запуска проекта.

2. Щелкните правой кнопкой мыши в первой закладке и нажмите кнопку **Полужирный**.

3. Убедитесь, что весь текст в `bookmark1` полужирным шрифтом.

4. Щелкните правой кнопкой мыши текст перекрытия закладки, а затем нажмите кнопку **курсив**.

5. Убедитесь, что весь текст в `bookmark2` и только часть текста в `bookmark1` , перекрывающуюся `bookmark2` отображается курсивом.

## <a name="next-steps"></a>Следующие шаги
 Ниже приводятся некоторые из возможных последующих задач.

- Напишите код для реагирования на события элементов управления ведущего приложения в Excel. Дополнительные сведения см. в разделе [Пошаговое руководство: Программа реакции на события элементов управления NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

- Использование типа "флажок" для изменения форматирования в закладке. Дополнительные сведения см. в разделе [Пошаговое руководство: Изменение форматирования документа с использованием элементов управления CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>См. также
- [Пошаговое руководство с использованием Word](../vsto/walkthroughs-using-word.md)
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)
- [Элемент управления Bookmark](../vsto/bookmark-control.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
