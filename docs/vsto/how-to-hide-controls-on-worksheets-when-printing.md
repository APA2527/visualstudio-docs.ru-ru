---
title: Как скрыть элементы управления на листах при печати
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 336723f60a2cd90dc63db24e981dd06e0388cb9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544811"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Как скрыть элементы управления на листах при печати
  При печати Microsoft Office документа Excel, содержащего элементы управления Windows Forms, элементы управления отображаются на распечатанном листе. Элементы управления можно скрывать при печати листа.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Если скрыть элементы управления, отображающие данные, например <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> , данные в элементе управления не будут видны на распечатанном листе.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Скрытие элементов управления при печати листа

1. Создайте или откройте проект Excel в Visual Studio и убедитесь, что элемент **Sheet1** виден в конструкторе. Сведения о создании проектов см. в разделе [Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. На вкладке **Общие элементы управления** **панели элементов**перетащите <xref:Microsoft.Office.Tools.Excel.Controls.Button> элемент управления в ячейку `Sheet1` .

3. В окне **Свойства** присвойте <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> свойству значение **false**.

## <a name="see-also"></a>См. также
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Общие сведения об элементах управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Добавление Windows Forms элементов управления в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Руководство. изменение размеров элементов управления в ячейках листа](../vsto/how-to-resize-controls-within-worksheet-cells.md)
