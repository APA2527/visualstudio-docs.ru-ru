---
title: Ведущий элемент книги
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel workbooks
- Workbook host items
- host items [Office development in Visual Studio], Workbook
- workbooks, Excel
- Workbook host items, events
- workbooks
- Excel [Office development in Visual Studio], workbooks
- workbooks, events
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 797f1a55ec7632114e411bf0ba08e7f4e0cc146e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255085"
---
# <a name="workbook-host-item"></a>Ведущий элемент книги
  Ведущий элемент <xref:Microsoft.Office.Tools.Excel.Workbook> является типом, который расширяет тип <xref:Microsoft.Office.Interop.Excel.Workbook> из основной сборки взаимодействия для Excel. Ведущий элемент <xref:Microsoft.Office.Tools.Excel.Workbook> предоставляет все свойства, методы и события объекта <xref:Microsoft.Office.Interop.Excel.Workbook> , но также предоставляет дополнительные компоненты.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 В проектах уровня документа имеется ведущий элемент <xref:Microsoft.Office.Tools.Excel.Workbook> по умолчанию, который представляет книгу в проекте. В проектах надстройки VSTO во время выполнения можно создавать ведущие элементы <xref:Microsoft.Office.Tools.Excel.Workbook> .

## <a name="understand-the-workbook-host-item-in-document-level-projects"></a>Знакомство с ведущим элементом книги в проектах уровня документа
 Для доступа к книге в проекте используйте класс `ThisWorkbook` . Класс `ThisWorkbook` обеспечивает доступ к членам ведущего элемента <xref:Microsoft.Office.Tools.Excel.Workbook> для выполнения основных задач по настройке, например для запуска кода при открытии или закрытии книги. Дополнительные сведения см. в разделе [Program настройки на уровне документа](../vsto/programming-document-level-customizations.md).

 Класс `ThisWorkbook` предоставляет место, в котором можно начать создание кода в проекте. Поскольку этот класс предоставляет все свойства, методы и события, что и объект <xref:Microsoft.Office.Interop.Excel.Workbook> в основной сборке взаимодействия для Excel, вы также можете использовать `ThisWorkbook` для доступа к объектной модели Excel. Дополнительные сведения см. в разделе [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md).

 Дважды щелкните элемент проекта **ThisWorkbook** в **обозревателе решений** , чтобы открыть конструктор книг и просмотреть свойства и события книги в окне **Свойства** .

### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>Ограничения ведущего элемента книги в проектах уровня документа
 Проект уровня документа может содержать только один ведущий элемент <xref:Microsoft.Office.Tools.Excel.Workbook> (то есть класс `ThisWorkbook` ). Вы не можете добавлять новые ведущие элементы <xref:Microsoft.Office.Tools.Excel.Workbook> в проект во время разработки и не можете создавать новые ведущие элементы <xref:Microsoft.Office.Tools.Excel.Workbook> во время выполнения в настройке уровня документа.

 При создании новой книги Excel во время выполнения она будет иметь тип <xref:Microsoft.Office.Interop.Excel.Workbook>. Поскольку это не ведущий элемент, он не может содержать никаких элементов управления ведущего приложения или элементов управления Windows Forms. Дополнительные сведения о создании книг во время выполнения см. в разделе [инструкции. Программное создание новых книг](../vsto/how-to-programmatically-create-new-workbooks.md).

 Ведущий элемент <xref:Microsoft.Office.Tools.Excel.Workbook> не действует как контейнер для элементов управления ведущего приложения. Таким образом, нельзя добавлять в книгу какие-либо видимые элементы управления, но можно добавлять компоненты, например <xref:System.Data.DataSet>, чтобы эти компоненты могли совместно использоваться всеми листами. В проекте уровня документа компоненты, доступные для книги, можно найти на вкладках **Компонент** , **Данные** и **Все формы Windows** в **панели элементов**.

> [!NOTE]
> Средства разработки Office в Visual Studio не поддерживают общие книги.

## <a name="understand-workbook-host-items-in-vsto-add-in-projects"></a>Общие сведения о ведущих элементах книги в проектах надстроек VSTO
 В проектах надстроек VSTO можно создавать ведущий элемент <xref:Microsoft.Office.Tools.Excel.Workbook> во время выполнения для любой книги, открытой в Excel. Для создания ведущего элемента <xref:Microsoft.Office.Tools.Excel.Workbook> используйте метод `GetVstoObject`. Дополнительные сведения см. [в разделе Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>См. также раздел
- [Примеры и пошаговые руководства по разработке решений Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Ведущий элемент листа](../vsto/worksheet-host-item.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
