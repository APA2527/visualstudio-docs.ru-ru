---
title: Практическое руководство. Добавление определенного метода Finder | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8fdd467f2b3a06398198f6fd8452c6a548bf0872
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431273"
---
# <a name="how-to-add-a-specific-finder-method"></a>Практическое руководство. Добавление определенного метода Finder
  Может возвращать отдельного экземпляра сущности, создав *специальный метод поиска* метод. Служба бизнес-данным (BDC) выполняется конкретный метод поиска, когда пользователь выбирает сущности в веб-части бизнес-данных или внешний список. Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-specific-finder-method"></a>Чтобы создать конкретный метод поиска

1. На **конструкторе BDC**, выберите сущность.

    Сведения о том, как добавить сущность к **конструкторе BDC** в Visual Studio, см. в разделе [как: Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. В строке меню выберите **представление** > **Other Windows**, **Подробности метода BDC**.

    **Подробности метода BDC** откроется окно. Дополнительные сведения об этом окне см. в разделе [Обзор средства конструирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. В **добавьте метод** выберите **создать конкретный метод поиска**.

    Visual Studio добавляет следующие элементы модели. Эти элементы появляются в **Подробности метода BDC** окна.

   - Метод.

   - Входной параметр для метода.

   - Возвращаемый параметр для метода.

   - Дескриптор типа для каждого параметра.

   - Экземпляр метода для метода.

     Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

4. Откройте Visual Studio **свойства** окна.

5. Настройте дескриптор типа значения, возвращаемого в качестве дескриптора типа сущности. Сведения о создании дескриптора типа сущности, см. в разделе [как: Определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Не нужно выполнить этот шаг, если вы добавили в метод Finder к сущности. Visual Studio использует дескриптор типа, определенного в методе поиска.

   > [!NOTE]
   > Если поле идентификатора типа сущности представляет поле в таблицу базы данных, который создается автоматически, задайте **только для чтения** поля идентификатора значение **True**.

6. В **сведения о методе** окно, выберите экземпляр для данного метода.

7. В **окно "Свойства"**, задайте **имя возвращаемого параметра** имя возвращаемого параметра метода. Дополнительные сведения о свойствах экземпляра метода, см. в разделе [экземпляр метода](http://go.microsoft.com/fwlink/?LinkID=169282).

8. В **обозревателе решений**, откройте контекстное меню файла кода службы, созданный для сущности и затем выберите **Просмотр кода**.

    В редакторе кода открывается файл кода службы сущности. Дополнительные сведения о файле код службы сущности, см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

9. Добавьте код конкретный метод поиска. Этот код выполняет следующие задачи:

   - Извлекает записи из источника данных.

   - Возвращает сущности для службы BDC.

     В следующем примере возвращается контакт из образца базы данных AdventureWorks для SQL Server.

     > [!NOTE]
     > Замените значение `ServerName` поле с именем сервера.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="see-also"></a>См. также
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Практическое руководство. Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Практическое руководство. Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Практическое руководство. Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Практическое руководство. Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Практическое руководство. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)
