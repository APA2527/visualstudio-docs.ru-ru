---
title: Практическое руководство. Сопоставление схем и листов внутри Visual Studio
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 80a19924aaf4fa0afe8e809006ada7fada0288f3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428118"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Практическое руководство. Сопоставление схем и листов внутри Visual Studio
  На лист можно сопоставить схему XML, когда лист открыт в среде Visual Studio. Можно использовать те же средства Microsoft Office Excel, которые используются, если книга открыта вне Visual Studio. Проект Office создает те же объекты ли сопоставления схемы с листом до или после создания решения Excel.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Составные XML-схемы нельзя использовать в решениях Excel.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Для сопоставления схемы XML в лист Excel в Visual Studio

1. Откройте книгу или шаблон проекта Excel в Visual Studio.

2. Выберите лист, чтобы переместить фокус в конструктор.

3. На ленте перейдите на вкладку **Разработчик** .

    > [!NOTE]
    > Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [Как Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. В **XML** щелкните **источника**.

     **Источник XML** откроется окно.

5. В **источник XML** окно, нажмите кнопку **карт XML**.

     **Карт XML** откроется диалоговое окно.

6. В **карт XML** диалоговом окне щелкните **добавить**.

7. Перейдите к нужному файлу схемы, выберите его и нажмите кнопку **откройте**.

8. Нажмите кнопку **ОК**.

     Схема представлена в **источник XML** окна. В проекте, типизированный <xref:System.Data.DataSet> создается на основе схемы и <xref:System.Windows.Forms.BindingSource> создается.

9. Перетащите элементы с **источник XML** окно до запятой на листе, в которой будут создаваться соответствующие элементы управления.

     Если перетащить элемент схемы неповторяющихся Office проекта приводит к возникновению ошибки <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> элемент управления, который автоматически привязывается к <xref:System.Windows.Forms.BindingSource>.

     При перетаскивании повторяющегося элемента схемы Office проекта приводит к возникновению ошибки <xref:Microsoft.Office.Tools.Excel.ListObject> элемент управления, который автоматически не привязан к источнику данных. Дополнительные сведения см. в разделе [XML-схем и данных в настройки уровня документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md).

## <a name="see-also"></a>См. также
- [Практическое руководство. Сопоставление схем и документов Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [XML-схемы и данные в настройках уровня документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
