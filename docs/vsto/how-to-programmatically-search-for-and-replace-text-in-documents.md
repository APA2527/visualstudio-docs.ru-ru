---
title: Поиск и замена текста в документах программным способом
description: Узнайте, как можно использовать Visual Studio для программного поиска и замены текста в документе Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f3ef1a32d145169db815915ee93d03893943e71f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877906"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>Руководство. Программный поиск и замена текста в документах
  Объект <xref:Microsoft.Office.Interop.Word.Find> является членом объектов <xref:Microsoft.Office.Interop.Word.Selection> и <xref:Microsoft.Office.Interop.Word.Range>, каждый из которых можно использовать для поиска текста в документах Microsoft Office Word. Команда замены является расширением команды поиска.

 С помощью объекта <xref:Microsoft.Office.Interop.Word.Find> можно выполнять операцию перебора документа Microsoft Office Word и поиска конкретного текста, форматирования или стиля, а свойство <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> можно использовать для замены всех найденных элементов.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-a-selection-object"></a>Использование объекта Selection
 При использовании объекта <xref:Microsoft.Office.Interop.Word.Selection> для поиска текста все заданные условия применяются только для поиска текущего выделенного текста. Если точкой вставки является <xref:Microsoft.Office.Interop.Word.Selection>, то поиск выполняется по документу. Если будет найден элемент, соответствующий условиям поиска, он будет автоматически выделен.

 Следует отметить, что условия <xref:Microsoft.Office.Interop.Word.Find> являются накопительными. Это означает, что условия добавляются к предыдущим условиям поиска. Для сброса форматирования из предыдущих операций поиска перед выполнением нового поиска используйте метод <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A>.

### <a name="to-find-text-using-a-selection-object"></a>Поиск текста с помощью объекта Selection

1. Назначьте переменной строку поиска.

    [!code-vb[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#68)]
    [!code-csharp[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#68)]

2. Сбросьте форматирование из предыдущих операций поиска.

    [!code-vb[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#69)]
    [!code-csharp[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#69)]

3. Выполните поиск и отобразите окно сообщения с результатами.

    [!code-vb[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#70)]
    [!code-csharp[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#70)]

   В следующем примере показан полный метод.

   [!code-vb[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#67)]
   [!code-csharp[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#67)]

## <a name="use-a-range-object"></a>Использование объекта Range
 Объект <xref:Microsoft.Office.Interop.Word.Range> позволяет искать текст, ничего не отображая в пользовательском интерфейсе. <xref:Microsoft.Office.Interop.Word.Find>Объект возвращает **значение true** , если найден текст, соответствующий условиям поиска, и **false** , если это не так. Он также переопределяет объект <xref:Microsoft.Office.Interop.Word.Range>, чтобы он соответствовал условиям поиска при обнаружении текста.

### <a name="to-find-text-using-a-range-object"></a>Поиск текста с помощью объекта Range

1. Определите объект <xref:Microsoft.Office.Interop.Word.Range>, состоящий из второго абзаца в документе.

    Следующий пример кода можно использовать в настройке на уровне документа.

    [!code-vb[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#72)]

    Следующий пример кода можно использовать в надстройке VSTO. В этом примере используется активный документ.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#72)]

2. С помощью <xref:Microsoft.Office.Interop.Word.Range.Find%2A> свойства <xref:Microsoft.Office.Interop.Word.Range> объекта сначала очистите все существующие параметры форматирования, а затем найдите строку **Find Me**.

    [!code-vb[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#73)]
    [!code-csharp[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#73)]

3. Отобразите результаты поиска в окне сообщения и выберите <xref:Microsoft.Office.Interop.Word.Range>, чтобы сделать его видимым.

    [!code-vb[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#74)]
    [!code-csharp[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#74)]

    Если поиск заканчивается неудачно, выбирается второй абзац. При успешном выполнении поиска отображаются условия поиска.

   В следующем примере показан полный код для настройки на уровне документа. Чтобы использовать этот пример, запустите код из класса `ThisDocument` в своем проекте.

   [!code-vb[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#71)]

   В следующем примере показан полный код для надстройки VSTO. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

   [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#71)]

## <a name="search-for-and-replace-text-in-documents"></a>Поиск и замена текста в документах
 Следующий код выполняет поиск в текущем выделенном фрагменте и заменяет все вхождения строки **Find Me** **найденной** строкой.

### <a name="to-search-for-and-replace-text-in-documents"></a>Поиск и замена текста в документах

1. Добавьте следующий пример кода в класс `ThisDocument` или `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#75)]
     [!code-csharp[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#75)]

     Класс <xref:Microsoft.Office.Interop.Word.Find> имеет метод <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A>, а класс <xref:Microsoft.Office.Interop.Word.Replacement> также имеет свой собственный метод <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A>. При выполнении операций Find-and-Replace необходимо использовать метод Клеарформаттинг обоих объектов. Если его использовать только на объекте <xref:Microsoft.Office.Interop.Word.Find>, то при замене текста можно получить непредвиденные результаты.

2. Для замены каждого найденного элемента используйте метод <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> объекта <xref:Microsoft.Office.Interop.Word.Find>. Чтобы указать, какие элементы следует заменить, используйте параметр *Replace* . Этот параметр может принимать одно из следующих значений <xref:Microsoft.Office.Interop.Word.WdReplace>:

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> заменяет все найденные элементы.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> не заменяет никакие найденные элементы.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> заменяет первый найденный элемент.

## <a name="see-also"></a>См. также раздел
- [Как программно задать параметры поиска в Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Пошаговое руководство. Программный перебор найденных элементов в документах](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Руководство. Программное определение и выбор диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Как программным способом восстановить выделенные элементы после поиска](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
