---
title: Практическое руководство. Отображение вкладки разработчика на ленте
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6a9a11f42acae44c441aca8cb06a1a363fea5a73
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418856"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Практическое руководство. Отображение вкладки разработчика на ленте
  Чтобы получить доступ к **разработчика** вкладку на ленте приложения Office, необходимо настроить его, чтобы отобразить эту вкладку, так как он не отображается по умолчанию. Например, необходимо отобразить эту вкладку, если требуется добавить <xref:Microsoft.Office.Tools.Word.GroupContentControl> в настройку уровня документа для Word.

> [!NOTE]
> Это руководство применимо только к приложениям Office 2010 или более поздней версии. Если вы хотите отобразить эту вкладку в системе 2007 Microsoft Office, см. следующую версию этого раздела [как: Отображение вкладки разработчика на ленте](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> Не имеет доступа **разработчика** вкладки.

## <a name="to-show-the-developer-tab"></a>Отображение вкладки "Разработчик"

1. Запустите любое приложение Office, указанное в этом разделе. См. в разделе **применяется к:** примечание выше в этом разделе.

2. На **файл** вкладке, выберите **параметры** кнопки.

     На следующем рисунке показан **файл** вкладку и **параметры** кнопки в Office 2010.

     ![Выбор файла, параметры в Outlook 2010](../vsto/media/vsto-office-file-tab.png "выбора файла, параметры в Outlook 2010")

     На следующем рисунке показан **файл** вкладку в Office 2013.

     ![Вкладка "файл" в Outlook 2013](../vsto/media/vsto-office2013-filetab.png "вкладка \"файл\" в Outlook 2013")

     На следующем рисунке показан **параметры** кнопки в Office 2013.

     ![Кнопка "Параметры" в Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "кнопка \"Параметры\" в Outlook 2013 Preview")

3. В _ApplicationName_**параметры** диалоговое окно, выберите **Настройка ленты** кнопки.

     На следующем рисунке показан **параметры** диалоговое окно и **Настройка ленты** кнопки в Excel 2010. Расположение этой кнопки аналогично и во всех остальных приложениях, перечисленных в приведенном выше подразделе "Применимо к".

     ![Настройка ленты кнопки](../vsto/media/vsto-office2010-customizeribbonbutton.png "кнопку Настройка ленты")

4. В списке основных вкладок выберите **разработчика** "флажок".

     На следующем рисунке показан **разработчика** "флажок" в Word 2010 и [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Расположение этого флажка аналогично и во всех остальных приложениях, перечисленных в приведенном выше подразделе "Применимо к".

     ![Флажок "Разработчик" в диалоговом окне Параметры Word](../vsto/media/vsto-office2010-developercheckbox.png "флажок \"Разработчик\" в диалоговом окне Параметры Word")

5. Выберите **ОК** кнопку, чтобы закрыть **параметры** диалоговое окно.

## <a name="see-also"></a>См. также
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
