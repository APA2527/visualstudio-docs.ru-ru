---
title: Руководство. Программное применение цвета к диапазонам Excel
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0d4a99e2e71e6a87b304ceea45a3cd595f911ff1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543459"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Руководство. Программное применение цвета к диапазонам Excel
  Чтобы применить цвет к тексту внутри диапазона ячеек, используйте <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления или собственный объект диапазона Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Использование элемента управления NamedRange
 Этот пример предназначен для настроек на уровне документа.

### <a name="to-apply-color-to-a-namedrange-control"></a>Применение цвета к элементу управления NamedRange

1. Создание <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления в ячейке a1.

     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]

2. Задает цвет текста в <xref:Microsoft.Office.Tools.Excel.NamedRange> элементе управления.

     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]

## <a name="use-native-excel-ranges"></a>Использовать собственные диапазоны Excel

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Применение цвета к объекту в собственном диапазоне Excel

1. Создайте диапазон в ячейке a1, а затем задайте цвет текста.

     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]

## <a name="see-also"></a>См. также раздел
- [Работа с диапазонами](../vsto/working-with-ranges.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Как программно ссылаться на диапазоны листов в коде](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
