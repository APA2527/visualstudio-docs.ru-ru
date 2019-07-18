---
title: Практическое руководство. Программное перечисление всех листов в книге
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing worksheets
- worksheets, listing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2153091b2b2abae05bf6f6c7856d2fa6d43f8967
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812428"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Практическое руководство. Программное перечисление всех листов в книге
  Класс <xref:Microsoft.Office.Interop.Excel.Workbook> предоставляет объект <xref:Microsoft.Office.Interop.Excel.Worksheets>. Этот объект содержит коллекцию всех объектов <xref:Microsoft.Office.Interop.Excel.Worksheet> в книге.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>Составление списка существующих в книге листов в настройке уровня документа

1. Следует выполнить итерацию коллекции <xref:Microsoft.Office.Interop.Excel.Worksheets> и отправить имя каждого листа в смещение ячейки из элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange>.

     [!code-csharp[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#21)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>Составление списка существующих в книге листов в надстройке VSTO

1. Следует выполнить итерацию коллекции <xref:Microsoft.Office.Interop.Excel.Worksheets> и отправить имя каждого листа в смещение ячейки из объекта <xref:Microsoft.Office.Interop.Excel.Range>.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>См. также
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Практическое руководство. Программное добавление новых листов в книги](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Практическое руководство. Программное перемещение листов в книгах](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
