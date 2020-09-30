---
title: Как программно вкладывать файлы в сообщения электронной почты Outlook
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2427ffc634976462e27eb788259184ce69347769
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585331"
---
# <a name="how-to-programmatically-attach-files-to-outlook-email-items"></a>Как программно вкладывать файлы в сообщения электронной почты Outlook
  В этом примере файл подключается к новому почтовому элементу и отправляется в Армандо Pinto. В примере предполагается, что в качестве получателя существует пользователь с именем Армандо Pinto.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_Outlook_RL_AttachFiles#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_AttachFiles/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_AttachFiles#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_AttachFiles/thisaddin.vb#1)]

## <a name="see-also"></a>См. также
- [Работа с элементами почты](../vsto/working-with-mail-items.md)
- [Руководство. Программная отправка электронной почты](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Как программно сохранять вложения из сообщений электронной почты Outlook](../vsto/how-to-programmatically-save-attachments-from-outlook-e-mail-items.md)
- [Руководство. Программное создание элемента электронной почты](../vsto/how-to-programmatically-create-an-e-mail-item.md)
