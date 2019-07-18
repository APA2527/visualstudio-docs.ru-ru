---
title: Пошаговое руководство. Изменение кэшированных данных в книгу на сервере
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], changing server data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f9bd70b2f89f748e1af9f4b291ecf1bddb4cc6c
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824285"
---
# <a name="walkthrough-change-cached-data-in-a-workbook-on-a-server"></a>Пошаговое руководство. Изменение кэшированных данных в книгу на сервере
  В этом пошаговом руководстве показано, как изменить набор данных, который кэшируется в книге Microsoft Office Excel без запуска Excel с помощью <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 В данном пошаговом руководстве рассмотрены следующие задачи:

- Определение набора данных, содержащий данные из базы данных AdventureWorksLT.

- Создание экземпляров набора данных в проекте книги Excel и проект консольного приложения.

- Создание <xref:Microsoft.Office.Tools.Excel.ListObject> , привязанных к набору данных в книге и заполнение <xref:Microsoft.Office.Tools.Excel.ListObject> с данными при открытии книги.

- Добавление набора данных в книге в кэш данных.

- Изменение столбца данных в кэшированный набор данных, выполнив код в консольном приложении без запуска Excel.

  Несмотря на то, что в этом пошаговом руководстве предполагается, что код выполняется на компьютере разработчика, код, рассмотренные в этом пошаговом руководстве можно использовать на сервере, который не установлен Excel.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Доступ к запущенному экземпляру Microsoft SQL Server или Microsoft SQL Server Express, имеющий пример базы данных AdventureWorksLT, подключенные к ней. Можно загрузить базу данных AdventureWorksLT с [веб-сайте CodePlex](http://go.microsoft.com/fwlink/?linkid=87843). Дополнительные сведения о подключении базы данных см. в следующих разделах:

  - Присоединение базы данных с помощью SQL Server Management Studio или SQL Server Management Studio Express, см. в разделе [как: Присоединение базы данных (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Присоединение базы данных с помощью командной строки, см. в разделе [как: Добавить файл базы данных для SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Создайте проект библиотеки классов, который определяет набор данных
 Чтобы использовать тот же набор данных в проекте книги Excel и консольное приложение, необходимо определить набор данных в отдельной сборке, на который ссылается оба проекта. В этом пошаговом руководстве необходимо определите набор данных в проекте библиотеки классов.

### <a name="to-create-the-class-library-project"></a>Чтобы создать проект библиотеки классов

1. Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

3. В области шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем нажмите кнопку **Windows**.

4. В списке шаблонов проектов выберите **библиотеки классов**.

5. В **имя** введите **AdventureWorksDataSet**.

6. Нажмите кнопку **Обзор**, перейдите к вашей *документов %UserProfile%\My* (для Windows XP и более ранних версий) или *%UserProfile%\Documents* (для Windows Vista) папки, а затем нажмите кнопку **Выберите папку**.

7. В **новый проект** диалоговое окно, убедитесь, что **создать каталог для решения** флажок не установлен.

8. Нажмите кнопку **ОК**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **AdventureWorksDataSet** проект **обозревателе решений** и открывает **Class1.cs** или **Class1.vb** файл кода.

9. В **обозревателе решений**, щелкните правой кнопкой мыши **Class1.cs** или **Class1.vb**, а затем нажмите кнопку **удалить**. Этот файл не обязательно для данного пошагового руководства.

## <a name="define-a-dataset-in-the-class-library-project"></a>Определить набор данных в проекте библиотеки классов
 Определите типизированный набор данных, содержащий данные из базы данных AdventureWorksLT для SQL Server 2005. Далее в этом пошаговом руководстве будет ссылаться на этот набор данных в проекте книги Excel и проект консольного приложения.

 Набор данных является *типизированный набор данных* , представляющий данные в таблице Product базы данных AdventureWorksLT. Дополнительные сведения о типизированных наборах данных см. в разделе [средства набора данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Для определения типизированного набора данных в проекте библиотеки классов

1. В **обозревателе решений**, нажмите кнопку **AdventureWorksDataSet** проекта.

2. Если **источников данных** окно не отображается, откройте его в строке меню выберите **представление** > **Other Windows**  >   **Источники данных**.

3. Выберите команду **Добавить новый источник данных** , чтобы запустить **Мастер настройки источника данных**.

4. Щелкните **База данных**и нажмите кнопку **Далее**.

5. Если имеется существующее подключение к базе данных AdventureWorksLT, выберите его и нажмите кнопку **Далее**.

    В противном случае нажмите **Создать подключение**и в диалоговом окне **Добавление подключения** создайте новое подключение. Дополнительные сведения см. в разделе [Добавление новых подключений](../data-tools/add-new-connections.md).

6. На странице **Сохранение подключения в файле конфигурации приложения** нажмите кнопку **Далее**.

7. В **Choose Your Database Objects** странице, разверните узел **таблиц** и выберите **продукт (SalesLT)** .

8. Нажмите кнопку **Готово**.

    *AdventureWorksLTDataSet.xsd* добавляется файл **AdventureWorksDataSet** проекта. В этом файле определены следующие элементы:

   - Типизированный набор данных с именем `AdventureWorksLTDataSet`. Этот набор данных представляет содержимое таблицы Product в базе данных AdventureWorksLT.

   - Адаптер таблицы с именем `ProductTableAdapter`. Этот адаптер таблицы можно использовать для чтения и записи данных `AdventureWorksLTDataSet`. Дополнительные сведения см. в разделе [TableAdapter overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Далее в пошаговом руководстве используются оба эти объекта.

9. В **обозревателе решений**, щелкните правой кнопкой мыши **AdventureWorksDataSet** и нажмите кнопку **построения**.

     Убедитесь, что сборка проекта выполняется без ошибок.

## <a name="create-an-excel-workbook-project"></a>Создание проекта книги Excel
 Создайте проект книги Excel для интерфейса к данным. Далее в этом пошаговом руководстве вы создадите <xref:Microsoft.Office.Tools.Excel.ListObject> , отображающий данные, и вы добавите экземпляр набора данных в кэш данных в книге.

### <a name="to-create-the-excel-workbook-project"></a>Создание проекта книги Excel

1. В **обозревателе решений**, щелкните правой кнопкой мыши **AdventureWorksDataSet** решение, выберите пункт **добавить**, а затем нажмите кнопку **новый проект**.

2. В области шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем разверните **Office**.

3. В развернутом **Office** выберите **2010** узла.

4. В списке шаблонов проектов выберите проект книги Excel.

5. В **имя** введите **AdventureWorksReport**. Не изменяйте расположение.

6. Нажмите кнопку **ОК**.

     Откроется **Мастер проектов набора средств Visual Studio для Office** .

7. Убедитесь, что **создания документа** выбран и нажмите кнопку **ОК**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Открывает **AdventureWorksReport** книгу в конструкторе и добавляет **AdventureWorksReport** проект **обозревателе решений**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Добавление набора данных к источникам данных в проекте книги Excel
 Прежде чем можно отобразить набор данных в книге Excel, необходимо сначала добавить набор данных к источникам данных в проекте книги Excel.

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Добавление набора данных к источникам данных в проекте книги Excel

1. В **обозревателе решений**, дважды щелкните **Sheet1.cs** или **Sheet1.vb** под **AdventureWorksReport** проекта.

     Книга откроется в конструкторе.

2. В меню **Данные** выберите команду **Добавить новый источник данных**.

     Открывается **мастер настройки источника данных**.

3. Нажмите кнопку **объект**, а затем нажмите кнопку **Далее**.

4. В **Выбор объекта для привязки к** щелкните **добавить ссылку**.

5. На **проекты** щелкните **AdventureWorksDataSet** и нажмите кнопку **ОК**.

6. В разделе **AdventureWorksDataSet** пространство имен **AdventureWorksDataSet** сборки, щелкните **AdventureWorksLTDataSet** и нажмите кнопку **Готово** .

     **Источников данных** откроется окно, и **AdventureWorksLTDataSet** добавляется в список источников данных.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Создайте элемент управления ListObject, привязанного к экземпляру набора данных
 Чтобы отобразить набор данных в книге, создайте <xref:Microsoft.Office.Tools.Excel.ListObject> , привязанный к экземпляру набора данных. Дополнительные сведения о привязке элементов управления к данным см. в разделе [привязки данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Чтобы создать элемент управления ListObject, привязанного к экземпляру набора данных

1. В **источников данных** окне разверните **AdventureWorksLTDataSet** узле **AdventureWorksDataSet**.

2. Выберите **продукта** узел, щелкните стрелку раскрывающегося списка, который отображается и выберите **ListObject** в раскрывающемся списке.

     Если стрелку раскрывающегося списка не отображается, убедитесь, что книга открыта в конструкторе.

3. Перетащите **продукта** таблицы в ячейку A1.

     Объект <xref:Microsoft.Office.Tools.Excel.ListObject> управления с именем `productListObject` создается на листе с началом в ячейку A1. Одновременно в проект добавляется объект набора данных `adventureWorksLTDataSet` и объект <xref:System.Windows.Forms.BindingSource> с именем `productBindingSource` . Объект <xref:Microsoft.Office.Tools.Excel.ListObject> привязан к объекту <xref:System.Windows.Forms.BindingSource>, который в свою очередь привязан к объекту набора данных.

## <a name="add-the-dataset-to-the-data-cache"></a>Добавление набора данных в кэше данных
 Чтобы включить кода за пределами проекта книги Excel, доступ к набору данных в книге, необходимо добавить набор данных в кэш данных. Дополнительные сведения о кэше данных, см. в разделе [кэшированных данных в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md) и [кэшировать данные](../vsto/caching-data.md).

### <a name="to-add-the-dataset-to-the-data-cache"></a>Добавление набора данных в кэше данных

1. В конструкторе щелкните **adventureWorksLTDataSet**.

2. В **свойства** окне **модификаторы** свойства **открытый**.

3. Задайте **CacheInDocument** свойства **True**.

## <a name="initialize-the-dataset-in-the-workbook"></a>Инициализации набора данных в книге
 Прежде чем можно получить данные из кэшированный набор данных с помощью консольного приложения, необходимо заполнить кэшированный набор данных с данными.

### <a name="to-initialize-the-dataset-in-the-workbook"></a>Для инициализации набора данных в книге

1. В **обозревателе решений**, щелкните правой кнопкой мыши **Sheet1.cs** или **Sheet1.vb** файл и нажмите кнопку **Просмотр кода**.

2. Замените обработчик событий `Sheet1_Startup` следующим кодом. Этот код использует экземпляр `ProductTableAdapter` класс, который определен в **AdventureWorksDataSet** проекта для заполнения кэшированный набор данных с данными, если он пуст.

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>Контрольная точка
 Постройте и запустите проект книги Excel, чтобы убедиться, что он компилируется и выполняется без ошибок. Эта операция также заполняет набор и сохраняет данные в книге.

### <a name="to-build-and-run-the-project"></a>Построение и запуск проекта

1. В **обозревателе решений**, щелкните правой кнопкой мыши **AdventureWorksReport** проекта, выберите **Отладка**, а затем нажмите кнопку **запустить новый экземпляр**.

     Проект будет собран и книга откроется в Excel. Проверьте следующее.

    - <xref:Microsoft.Office.Tools.Excel.ListObject> Заполняется данными.

    - Значение в **ListPrice** столбец для первой строки <xref:Microsoft.Office.Tools.Excel.ListObject> равно 1431,5. Далее в этом пошаговом руководстве будет использовать консольное приложение для изменения значений во **ListPrice** столбца.

2. Сохраните книгу. Не изменяйте имя файла или расположение книги.

3. Закройте Excel.

## <a name="create-a-console-application-project"></a>Создайте проект консольного приложения
 Создайте проект консольного приложения для использования для изменения данных в кэшированный набор данных в книге.

### <a name="to-create-the-console-application-project"></a>Чтобы создать проект консольного приложения

1. В **обозревателе решений**, щелкните правой кнопкой мыши **AdventureWorksDataSet** решение, выберите пункт **добавить**, а затем нажмите кнопку **новый проект**.

2. В **типы проектов** панели разверните **Visual C#** или **Visual Basic**, а затем нажмите кнопку **Windows**.

3. В **шаблоны** области выберите **консольное приложение**.

4. В **имя** введите **DataWriter**. Не изменяйте расположение.

5. Нажмите кнопку **ОК**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **DataWriter** проект **обозревателе решений** и открывает **Program.cs** или **Module1.vb** файл кода.

## <a name="change-data-in-the-cached-dataset-by-using-the-console-application"></a>Изменять данные в кэшированный набор данных с помощью консольного приложения
 Используйте <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класс в консольном приложении для считывания данных в локальный `AdventureWorksLTDataSet` объекта, изменить эти данные и затем сохранить их обратно кэшированный набор данных.

### <a name="to-change-data-in-the-cached-dataset"></a>Для изменения данных в кэшированный набор данных

1. В **обозревателе решений**, щелкните правой кнопкой мыши **DataWriter** проекта и нажмите кнопку **добавить ссылку**.

2. На **.NET** выберите **Microsoft.VisualStudio.Tools.Applications**.

3. Нажмите кнопку **ОК**.

4. В **обозревателе решений**, щелкните правой кнопкой мыши **DataWriter** проекта и нажмите кнопку **добавить ссылку**.

5. На **проекты** выберите **AdventureWorksDataSet**и нажмите кнопку **ОК**.

6. Откройте *Program.cs* или *Module1.vb* файл в редакторе кода.

7. Добавьте следующий **с помощью** (для C#) или **Imports** (для Visual Basic) в начало файла кода.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. Добавьте следующий код в метод `Main` . Этот код объявляет следующие объекты:

   - Экземпляр `AdventureWorksLTDataSet` тип, определенный в **AdventureWorksDataSet** проекта.

   - Путь к книге AdventureWorksReport в папке сборки **AdventureWorksReport** проекта.

   - Объект <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> , который используется для доступа к кэшу данных в книге.

     > [!NOTE]
     > В следующем коде предполагается, что вы используете книге, в которой *.xlsx* расширение файла. Если книгу в проекте с расширением другой файл, измените путь соответственно.

     [!code-csharp[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#6)]
     [!code-vb[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#6)]

9. Добавьте следующий код, чтобы `Main` метод после кода, добавленного на предыдущем шаге. Этот код выполняет следующие задачи:

   - Она использует <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> свойство <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класс для доступа к кэшированный набор данных в книге.

   - Он считывает данные из кэшированного набора данных в локальный набор данных.

   - Он изменяет `ListPrice` значение для каждого продукта в таблице Product набора данных.

   - Сохраняет изменения в кэшированный набор данных в книге.

     [!code-csharp[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#7)]
     [!code-vb[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#7)]

10. В **обозревателе решений**, щелкните правой кнопкой мыши **DataWriter** проект, выберите пункт **Отладка**, а затем нажмите кнопку **запустить новый экземпляр**.

     Консольное приложение отображает сообщения, хотя он считывает кэшированный набор данных в локальный набор данных, изменяет цены продуктов в локальном наборе данных и сохраняет новые значения в кэшированный набор данных. Нажмите клавишу **ввод** закрыть приложение.

## <a name="test-the-workbook"></a>Проверка книги
 При открытии книги, <xref:Microsoft.Office.Tools.Excel.ListObject> теперь отображаются изменения, внесенные в `ListPrice` столбца данных в кэшированный набор данных.

### <a name="to-test-the-workbook"></a>Тестирование книги

1. Закрытие книги AdventureWorksReport в конструкторе Visual Studio, если он по-прежнему открыт.

2. Откройте книгу AdventureWorksReport, находится в папке построения **AdventureWorksReport** проекта. По умолчанию папке сборки находится в одном из следующих расположений:

    - *%USERPROFILE%\My Documents\AdventureWorksReport\bin\Debug* (для Windows XP и более ранних версий)

    - *%USERPROFILE%\Documents\AdventureWorksReport\bin\Debug* (для Windows Vista)

3. Убедитесь, что значение в **ListPrice** столбец для первой строки <xref:Microsoft.Office.Tools.Excel.ListObject> равно 1574,65.

4. Закройте книгу.

## <a name="see-also"></a>См. также

- [Пошаговое руководство: Вставка данных в книгу на сервере](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
