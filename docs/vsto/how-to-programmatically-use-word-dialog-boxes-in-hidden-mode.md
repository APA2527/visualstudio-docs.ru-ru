---
title: Руководство. программное использование диалоговых окон Word в скрытом режиме
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 923fc7ddec0350f254968fe17494ecbe27f76b13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537583"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Руководство. программное использование диалоговых окон Word в скрытом режиме
  Можно выполнять сложные операции с одним вызовом метода путем вызова встроенных диалоговых окон в Microsoft Office Word без отображения их пользователю. Это можно сделать с помощью <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> метода <xref:Microsoft.Office.Interop.Word.Dialog> объекта, не вызывая <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> метод.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Примеры
 В следующих примерах кода показано, как использовать диалоговое окно « **Параметры страницы** » в скрытом режиме для задания нескольких свойств настройки страницы без ввода данных пользователем. В примерах используется <xref:Microsoft.Office.Interop.Word.Dialog> объект для настройки пользовательского размера страницы. Конкретные параметры настройки страницы, такие как верхнее поле, нижнее поле и т. д., доступны в виде свойств объекта с поздним связыванием <xref:Microsoft.Office.Interop.Word.Dialog> . Эти свойства динамически создаются Word во время выполнения.

 В следующем примере показано, как выполнить эту задачу в Visual Basic проектах, в которых **параметр optioned** имеет значение OFF и в проектах Visual C#, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . В этих проектах можно использовать функции позднего связывания в компиляторах Visual Basic и Visual C#. Чтобы использовать этот пример, запустите его из `ThisDocument` класса или `ThisAddIn` в проекте.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 В следующем примере показано, как выполнить эту задачу в Visual Basic проектах, где **параметр Option-on** имеет значение ON. В этих проектах для доступа к свойствам с поздним связыванием необходимо использовать отражение. Чтобы использовать этот пример, запустите его из `ThisDocument` класса или `ThisAddIn` в проекте.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>См. также раздел
- [Руководство. программное использование встроенных диалоговых окон в Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)
- [Позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md)
- [Отражение (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection) (Отражение (Visual Basic))
