---
title: Практическое руководство. Программная печать листов Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 76315f6cde5bc54385e217a8f234389a7f45e621
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955928"
---
# <a name="how-to-programmatically-print-worksheets"></a>Практическое руководство. Программная печать листов Excel
  Любой лист в книге можно напечатать.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Печать листа в настройке уровня документа

### <a name="to-print-a-worksheet"></a>Печать листа

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> `Sheet1`, запросите две копии и просмотрите документ перед печатью.

    [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
    [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]

   <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> Метод позволяет отобразить указанный объект в **Предварительный просмотр печати** окна. В следующем коде предполагается, что существует ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> с именем `Sheet1`.

### <a name="to-preview-a-page-before-printing"></a>Предварительный просмотр страницы перед печатью

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> листа.

     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Печать листа в надстройке VSTO

### <a name="to-print-a-worksheet"></a>Печать листа

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> активного листа, запросите две копи и просмотрите документ перед печатью.

    [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
    [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]

   <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> Метод позволяет отобразить указанный объект в **Предварительный просмотр печати** окна.

### <a name="to-preview-a-page-before-printing"></a>Предварительный просмотр страницы перед печатью

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> активного листа.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>См. также
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Практическое руководство. Программная проверка орфографии на листах](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Ведущий элемент листа](../vsto/worksheet-host-item.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
