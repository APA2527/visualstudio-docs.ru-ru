---
title: Руководство. Программное определение текущего элемента Outlook
description: Узнайте, как программным способом определить текущий элемент Microsoft Outlook. В этом примере используется событие Explorer. SelectionChange.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 10b8bd8103e80040519b9e3c5546f892da326202
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526789"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Руководство. Программное определение текущего элемента Outlook
  В этом примере используется `Explorer.SelectionChange` событие для вывода имени текущей папки и некоторых сведений о выбранном элементе. Затем код отображает выбранный элемент.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Пример
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются:

- Встречи, контакты и элементы электронной почты в Microsoft Office Outlook.

## <a name="see-also"></a>См. также раздел
- [Общие сведения об объектной модели Outlook](../vsto/outlook-object-model-overview.md)
- [Как программно получить папку по имени](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Руководство. Программный поиск определенного контакта](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
