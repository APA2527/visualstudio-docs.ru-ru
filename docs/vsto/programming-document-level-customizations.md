---
title: Программирование настроек уровня документа
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Sheet3
- thisWorkbook
- thisDocument
- Sheet1
- Sheet2
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument class
- Sheet3 class
- ThisWorkbook class
- writing code for Office solutions
- programming [Office development in Visual Studio], document-level customizations
- Sheet1 class
- Office applications [Office development in Visual Studio], document-level customizations
- Sheet2 class
- document-level customizations [Office development in Visual Studio], programming
- application development [Office development in Visual Studio], document-level customizations
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 53003e2a88faf2ef29d3a1eb3df1da081f20ce57
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62561713"
---
# <a name="program-document-level-customizations"></a>Программирование настроек уровня документа
  При расширении приложения Microsoft Office Word или Microsoft Office Excel с помощью настройки уровня документа вы можете выполнять следующие задачи.

- Автоматизация приложения с помощью его объектной модели.

- Добавление элементов управления в документ.

- Вызов Visual Basic для кода приложений (VBA) в документе из сборки настройки.

- Вызов кода в сборке настройки из VBA.

- Управление определенными аспектами документа, если он находится на сервере, на котором не установлен Microsoft Office.

- Настройка пользовательского интерфейса приложения.

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  Некоторые аспекты создания кода в проектах уровня документов отличаются от работы с другими типами проектов в Visual Studio. Многие отличия связаны с тем, каким образом объектные модели Office предоставляются управляемому коду. Дополнительные сведения см. в разделе [написания кода в решениях Office](../vsto/writing-code-in-office-solutions.md).

  Общие сведения о настройках уровня документа и других типах решений, которые можно создавать с помощью средств разработки Office в Visual Studio, см. в разделе [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-generated-classes-in-document-level-projects"></a>Использование созданных классов в проектах уровня документа
 При создании проекта уровня документа Visual Studio автоматически создает в этом проекте класс, который можно использовать для начала создания кода. Visual Studio создает для Word и Excel разные классы.

- В проектах уровня документа для Word класс называется `ThisDocument` по умолчанию.

- Проекты уровня документа для Excel имеет несколько создаваемых классов: один для самой книги и по одному для каждого листа. По умолчанию эти классы имеют следующие имена:

  - `ThisWorkbook`

  - `Sheet1`

  - `Sheet2`

  - `Sheet3`

  Созданный класс содержит обработчики событий, которые вызываются при открытии или закрытии документа. Для выполнения кода при открытии документа добавьте код в обработчик событий `Startup` . Для выполнения кода непосредственно перед закрытием документа добавьте код в обработчик событий `Shutdown` . Дополнительные сведения см. в разделе [события в проектах Office](../vsto/events-in-office-projects.md).

### <a name="understand-the-design-of-the-generated-classes"></a>Понимание дизайна созданных классов
 В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], типами ведущих элементов в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] являются интерфейсы, поэтому создаваемые классы не могут наследовать от них свою реализацию. Вместо этого создаваемые классы наследуют большинство своих членов от следующих базовых классов.

- `ThisDocument`: производный от <xref:Microsoft.Office.Tools.Word.DocumentBase>.

- `ThisWorkbook`: производный от <xref:Microsoft.Office.Tools.Excel.WorkbookBase>.

- `Sheet` *n*: является производным от <xref:Microsoft.Office.Tools.Excel.WorksheetBase>.

  Эти базовые классы перенаправляют все вызовы своих членов во внутренние реализации соответствующих интерфейсов ведущих элементов в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Например, при вызове метода <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> класса `ThisDocument` класс <xref:Microsoft.Office.Tools.Word.DocumentBase> перенаправляет этот вызов во внутреннюю реализацию интерфейса <xref:Microsoft.Office.Tools.Word.Document> в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

## <a name="access-the-object-model-of-the-host-application"></a>Доступ к объектной модели ведущего приложения
 Для доступа к объектной модели ведущего приложения используйте члены создаваемого класса в проекте. Каждый из этих классов соответствует объекту в объектной модели Excel или Word, и они содержат большую часть тех же свойств, методов и событий. Например, класс `ThisDocument` в проекте уровня документа для Word содержит большую часть тех же элементов, что и объект <xref:Microsoft.Office.Interop.Word.Document> в объектной модели Word.

 В следующем примере кода показано, как использовать объектную модель Word для сохранения документа, который является частью настройки уровня документа для Word. Код в примере должен выполняться из класса `ThisDocument` .

```vb
Me.Save()
```

```csharp
this.Save();
```

 Чтобы выполнить это же действие без использования класса `ThisDocument` , используйте для получения доступа к классу `Globals` объект `ThisDocument` . Например, можно добавить этот код в файл кода области действий, если требуется включить кнопку **Сохранить** в пользовательский интерфейс панели действий.

```vb
Globals.ThisDocument.Save()
```

```csharp
Globals.ThisDocument.Save();
```

 Поскольку класс `ThisDocument` получает большинство своих членов от ведущего элемента <xref:Microsoft.Office.Tools.Word.Document> , метод `Save` , вызываемый в этом коде, фактически является методом <xref:Microsoft.Office.Tools.Word.Document.Save%2A> ведущего элемента <xref:Microsoft.Office.Tools.Word.Document> . Этот метод соответствует методу <xref:Microsoft.Office.Interop.Word._Document.Save%2A> объекта <xref:Microsoft.Office.Interop.Word.Document> в объектной модели Word.

 Дополнительные сведения об использовании объектных моделях Word и Excel см. в разделе [обзор объектной модели Word](../vsto/word-object-model-overview.md) и [обзор объектной модели Excel](../vsto/excel-object-model-overview.md).

 Дополнительные сведения о `Globals` объекта, см. в разделе [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).

## <a name="add-controls-to-documents"></a>Добавление элементов управления в документы
 Чтобы настроить пользовательский интерфейс документа, можно добавлять элементы управления Windows Forms или *элементы управления ведущего приложения* в область документа. Используя различные сочетания элементов управления и создавая код, можно привязать элементы управления к данным, собирать сведения от пользователя и реагировать на действия пользователя.

 Элементы управления ведущего приложения — это классы, которые расширяют некоторые объекты в объектных моделях Word и Excel. Например, элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.ListObject> предоставляет все функциональные возможности <xref:Microsoft.Office.Interop.Excel.ListObject> в Excel. Однако элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.ListObject> также имеет дополнительные события и возможности привязки данных.

 Дополнительные сведения см. в разделе [ведущие элементы и размещать элементы управления](../vsto/host-items-and-host-controls-overview.md) и [Windows forms, элементы управления на общие сведения о документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="combine-vba-and-document-level-customizations"></a>Объединение VBA и настроек уровня документа
 Вы можете использовать код VBA в документе, который является частью настройки уровня документа. Код VBA можно вызывать в документе из сборки настройки, или проект можно настроить таким образом, чтобы позволить коду VBA в документе вызывать код в сборке настройки.

 Дополнительные сведения см. в разделе [объединение VBA и настроек уровня документа](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="manage-documents-on-a-server"></a>Управление документами на сервере
 Вы можете управлять некоторыми аспектами настроек уровня документа на сервере, где не установлен Microsoft Office Word или Microsoft Office Excel. Например, можно получать доступ к данным в кэше данных документа и изменять их. Также можно управлять сборкой настройки, связанной с документом. Например, вы можете удалить сборку из документа программными средствами, чтобы документ больше не выполнял этот код, или прикрепить сборку к документу программными средствами.

 Дополнительные сведения см. в разделе [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Настройка пользовательского интерфейса приложений Microsoft Office
 С помощью настройки уровня документа вы можете настраивать пользовательский Интерфейс Word и Excel следующими способами.

- Добавление элементов управления ведущего приложения или элементов управления Windows Forms в область документа.

   Дополнительные сведения см. в разделе [автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md), [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md), и [элементы управления Windows Forms на общие сведения о документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

- Добавление панели действий в документ.

   Дополнительные сведения см. в разделе [Общие сведения о панели действий](../vsto/actions-pane-overview.md).

- Добавление настраиваемых вкладок на ленту.

   Дополнительные сведения см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).

- Добавление настраиваемых групп на встроенную вкладку на ленте.

   Дополнительные сведения см. в разделе [Как Настройка встроенной вкладки](../vsto/how-to-customize-a-built-in-tab.md).

  Дополнительные сведения о настройке пользовательского интерфейса Microsoft Office, см. в разделе [настройки пользовательского интерфейса Office](../vsto/office-ui-customization.md).

## <a name="get-extended-objects-from-native-office-objects-in-document-level-customizations"></a>Получение расширенных объектов из собственных объектов Office в настройках уровня документа
 Многие обработчики событий для событий Office получают собственный объект Office, представляющий книгу, лист или документ, который вызвал событие. В некоторых случаях может потребоваться выполнять определенный код только в том случае, если книга или документ в настройке уровня документа вызывает событие. Например, в настройке уровня документа для Excel вам может потребоваться выполнять определенный код, когда пользователь активирует один из листов в настраиваемой книге, но не в том случае, когда пользователь активирует лист в другой книге, которая была открыта одновременно.

 При наличии собственного объекта Office можно проверить, был ли этот объект расширен до *ведущего элемента* или *элемента управления ведущего приложения* в настройке уровня документа. Ведущие элементы и элементы управления ведущего приложения — это типы, предоставляемые средой выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , которые расширяют функциональные возможности объектов, существующих в объектных моделях Word или Excel (так называемых *собственных объектов Office*). Совместно ведущие элементы и элементы управления ведущего приложения также называются *расширенными объектами*. Дополнительные сведения о ведущих элементах и элементах управления ведущего приложения см. в разделе [ведущие элементы и размещать элементы управления](../vsto/host-items-and-host-controls-overview.md).

## <a name="understand-the-getvstoobject-and-hasvstoobject-methods"></a>Разобраться в методах GetVstoObject и HasVstoObject
 Чтобы протестировать собственный объект Office, используйте в своем проекте методы `HasVstoObject` и `GetVstoObject`.

- Используйте метод `HasVstoObject`, чтобы определить, имеет ли собственный объект Office расширенный объект в вашей настройке. Этот метод возвращает значение **true** , если собственный объект Office имеет расширенный объект, и значение **false** в противном случае.

- Используйте метод `GetVstoObject`, если нужно получить расширенный объект для собственного объекта Office. Этот метод возвращает объект <xref:Microsoft.Office.Tools.Excel.ListObject>, <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>или <xref:Microsoft.Office.Tools.Word.Document> , если его имеет указанный собственный объект Office. В противном случае `GetVstoObject` возвращает **null**. Например, метод `GetVstoObject` возвращает <xref:Microsoft.Office.Tools.Word.Document>, если указанный <xref:Microsoft.Office.Interop.Word.Document> является базовым объектом для документа в текущем проекте документа Word.

  В проектах уровня документа нельзя использовать `GetVstoObject` метод для создания нового <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>, или <xref:Microsoft.Office.Tools.Word.Document> ведущего элемента во время выполнения. Этот метод можно использовать только для доступа к существующим ведущим элементам, созданным в текущем проекте во время разработки. Если вы хотите создавать новые ведущие элементы во время выполнения, необходимо разработать проект надстройки VSTO. Дополнительные сведения см. в разделе [программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) и [документов расширения Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="use-the-getvstoobject-and-hasvstoobject-methods"></a>Использование методов GetVstoObject и HasVstoObject
 Для вызова `HasVstoObject` и `GetVstoObject` используйте `Globals.Factory.GetVstoObject` или `Globals.Factory.HasVstoObject` и передайте собственный объект Word или Excel (такие как <xref:Microsoft.Office.Interop.Word.Document> или <xref:Microsoft.Office.Interop.Excel.Worksheet>), которую требуется проверить.

## <a name="see-also"></a>См. также
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Объединение VBA и настроек уровня документа](../vsto/combining-vba-and-document-level-customizations.md)
- [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)
