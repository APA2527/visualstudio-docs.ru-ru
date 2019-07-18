---
title: Практическое руководство. Добавление элементов управления ListObject на листы
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5e7f82f667fffec09894ab65e277cea09d137a9b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62826713"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Практическое руководство. Добавление элементов управления ListObject на листы
  Вы можете добавить <xref:Microsoft.Office.Tools.Excel.ListObject> элементов управления на лист Microsoft Office Excel во время разработки и во время выполнения в проектах уровня документа.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Можно также добавить <xref:Microsoft.Office.Tools.Excel.ListObject> элементов управления во время выполнения в проектах надстройки VSTO.

 В этом разделе описываются следующие задачи.

- [Добавление элементов управления ListObject во время разработки](#designtime)

- [Добавление элементов управления ListObject во время выполнения в проекте уровня документа](#runtimedoclevel)

- [Добавление элементов управления ListObject во время выполнения в проекте надстройки VSTO](#runtimeaddin)

  Дополнительные сведения о <xref:Microsoft.Office.Tools.Excel.ListObject> элементов управления, см. в разделе [элемент управления ListObject](../vsto/listobject-control.md).

## <a name="designtime"></a> Добавление элементов управления ListObject во время разработки
 Существует несколько способов добавления <xref:Microsoft.Office.Tools.Excel.ListObject> элементов управления на лист в проекте уровня документа во время разработки: Из Excel, из Visual Studio **элементов**и из **источников данных** окна.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-use-the-ribbon-in-excel"></a>Использование ленты в Excel

1. На вкладке **Вставка** в группе **Таблицы** щелкните элемент **Таблица**.

2. Выделите ячейки, которые хотите включить в список, и нажмите кнопку **ОК**.

#### <a name="to-use-the-toolbox"></a>Использование панели элементов

1. Из вкладки **Элементы управления Excel** на **панели элементов**перетащите <xref:Microsoft.Office.Tools.Excel.ListObject> в лист.

     Откроется диалоговое окно **Добавление элемента управления ListObject** .

2. Выделите ячейки, которые хотите включить в список, и нажмите кнопку **ОК**.

     Если вы не хотите использовать имя по умолчанию, измените его в окне **Свойства** .

#### <a name="to-use-the-data-sources-window"></a>Использование окна "Источники данных".

1. Откройте окно **Источники данных** и создайте источник данных для проекта. Дополнительные сведения см. в разделе [Добавление новых подключений](../data-tools/add-new-connections.md).

2. Перетащите таблицу из окна **Источники данных** в лист.

     Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с привязкой к данным добавится на лист. Дополнительные сведения см. в разделе [привязка данных и Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="runtimedoclevel"></a> Добавление элементов управления ListObject во время выполнения в проекте уровня документа
 Вы можете добавить <xref:Microsoft.Office.Tools.Excel.ListObject> управления динамически во время выполнения. Это позволяет создавать элементы управления ведущего приложения при возникновении определенных событий. При закрытии листа динамически созданные объекты списка не сохраняются на листе как элементы управления ведущего приложения. Дополнительные сведения см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Добавление элемента управления ListObject в лист программными средствами

1. В обработчике событий <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> для `Sheet1`вставьте следующий код, чтобы добавить элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> в ячейки с **A1** до **A4**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]

## <a name="runtimeaddin"></a> Добавление элементов управления ListObject во время выполнения в проекте надстройки VSTO
 Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> можно добавить программным образом на любой открытый лист в проекте надстройки VSTO. При сохранении и закрытии листа динамически созданные объекты списка не сохраняются на листе как элементы управления ведущего приложения. Дополнительные сведения см. в разделе [документов расширения Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Добавление элемента управления ListObject в лист программными средствами

1. Следующий код создает ведущий элемент листа, который основан на открытом листе, а затем добавляет элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> в ячейки с **A1** до **A4**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]

## <a name="see-also"></a>См. также
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Элемент управления ListObject](../vsto/listobject-control.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)
- [Практическое руководство. Изменение размера элементов управления ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
