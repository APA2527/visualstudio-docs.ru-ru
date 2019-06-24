---
title: Начать & конец символов в диапазонах программным способом
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8e0f04d5f70c99ea3404a95b04a7ea668a37e0f2
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328946"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Практическое руководство. Извлечение знаков начала и завершения в диапазонах программным способом
  В этом примере показано, как получить позиции символов начала и конца диапазона.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Получение начального и конечного знаков диапазона в настройке уровня документа

1. Получите значения свойств <xref:Microsoft.Office.Interop.Word.Range.Start%2A> и <xref:Microsoft.Office.Interop.Word.Range.End%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> . В следующем примере кода возвращается позиция начала и конца второго предложения в документе. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Получение начального и конечного знаков диапазона с помощью надстройки VSTO

1. Получите значения свойств <xref:Microsoft.Office.Interop.Word.Range.Start%2A> и <xref:Microsoft.Office.Interop.Word.Range.End%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> . В следующем примере кода возвращается позиция начала и конца второго предложения в активном документе. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]

## <a name="see-also"></a>См. также
- [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Практическое руководство. Программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Практическое руководство. Программно сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Практическое руководство. Программное свертывание диапазонов и выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Практическое руководство. Программно exclude абзаца при создании диапазонов](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Практическое руководство. Программным способом подсчета символов в документах](../vsto/how-to-programmatically-count-characters-in-documents.md)
