---
title: Практическое руководство. Добавление существующего файла модели BDC в проект SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9c10dcf48e5c047778b86c524b35b4e1d5d8cc8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967057"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Практическое руководство. Добавление существующего файла модели BDC в проект SharePoint
  Можно настроить, упаковать и повторно развернуть модель бизнес-данным (BDC) с помощью Visual Studio для добавления файла модели (*.bdcm*) к любому проекту фермы SharePoint. Дополнительные сведения см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Добавление файла модели подключения к бизнес-данным (BDC) в проект SharePoint

1. В **обозревателе решений**, выберите папку для проекта SharePoint.

2. В строке меню выберите **проекта** > **добавить существующий элемент**.

3. В **добавить существующий элемент** диалоговое окно, перейдите к расположению файла определения модели, который требуется добавить в проект, выберите файл и нажмите кнопку **добавить** кнопки.

    Если модель не определяет *строки из БИЗНЕС-систему типа сборки .NET*, **бизнес-системы сборки .NET, добавьте** откроется диалоговое окно.

4. Если появится диалоговое окно, выполните одно из следующих действий.

   - Если вы хотите написать пользовательский код и использовать конструктор для определения метаданных для импортированной модели, выберите **Да** , назовите систему, а затем **ОК** кнопки.

   - В противном случае выберите **нет** кнопку, а затем выберите **ОК** кнопки.

     **Business Data Connectivity Model** элемент добавляется в проект.

## <a name="see-also"></a>См. также
- [Создание модели подключения к бизнес-данных](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Практическое руководство. Создать модель BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Практическое руководство. Использование файла ресурсов для задания локализованных имен, свойств и разрешений](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Практическое руководство. Добавление пользовательской сборки в возможность BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
