---
title: Руководство. Программное открытие книг
description: Узнайте, как можно использовать Visual Studio для программного открытия книги Microsoft Excel или работы с существующей книгой.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5bca39b5536d5717da994808f23ee541856264ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888736"
---
# <a name="how-to-programmatically-open-workbooks"></a>Руководство. Программное открытие книг
  <xref:Microsoft.Office.Interop.Excel.Workbooks>Коллекция в Microsoft Office Excel дает возможность работать со всеми открытыми книгами и открывать книги.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Открытие существующей книги

1. Используйте <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> метод <xref:Microsoft.Office.Interop.Excel.Workbooks> коллекции, передав в нее путь к книге.

     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера кода требуется следующее.

- Книга с именем `YourWorkbook.xls` должна находиться в каталоге с именем `Test` на диске C.

## <a name="see-also"></a>См. также раздел
- [Работа с книгами](../vsto/working-with-workbooks.md)
- [Руководство. Программное открытие текстовых файлов в виде книг](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Как создать новые книги программным способом](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Как программно сохранять книги](../vsto/how-to-programmatically-save-workbooks.md)
- [Руководство. программное закрытие книг](../vsto/how-to-programmatically-close-workbooks.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
