---
title: Как программно скрыть листы
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 83cf1f63a67525dca4cf9dbb5a4916da5d70b4ce
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547411"
---
# <a name="how-to-programmatically-hide-worksheets"></a>Как программно скрыть листы
  Вы можете отображать или скрывать любой лист в книге. Чтобы скрыть лист, используйте ведущий элемент листа или получите доступ к листу с помощью коллекции листов книги.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Использование ведущего элемента листа
 Если лист был добавлен в настройку уровня документа во время разработки, для скрытия указанного листа используйте свойство <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> .

### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Скрытие листа с помощью ведущего элемента листа

1. Установите в свойстве <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> ведущего элемента `Sheet1` значение перечисления <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .

     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Использование коллекции листов книги Excel
 Обращайтесь к листам с помощью коллекции <xref:Microsoft.Office.Interop.Excel.Sheets> для Microsoft Office Excel в следующих случаях.

- Необходимо скрыть лист в надстройке VSTO.

- Лист, который вы хотите скрыть, был создан во время выполнения в настройке уровня документа.

### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Скрытие листа с помощью коллекции листов книги Excel

1. Установите в свойстве <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> листа значение перечисления <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .

     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]

## <a name="see-also"></a>См. также раздел
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Руководство. Программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Руководство. Программное перемещение листов в книгах](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Как программно защитить листы](../vsto/how-to-programmatically-protect-worksheets.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
