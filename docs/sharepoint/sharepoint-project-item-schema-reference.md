---
title: Справочник по схеме элементов проекта SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc15ff5c384ec63f99ed50a5f3c700efd7ba3c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "63007723"
---
# <a name="sharepoint-project-item-schema-reference"></a>Справочник по схеме элементов проекта SharePoint
  Visual Studio использует схему элемента проекта SharePoint для проверки содержимого файлов *данных.* Файл *данных....* задает содержимое и поведение элемента проекта SharePoint. Дополнительные сведения о содержимом элементов проектов SharePoint см. в разделе [Создание шаблонов элементов и шаблонов проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Схема элемента проекта SharePoint называется Прожектитеммоделсчема. xsd и устанавливается по умолчанию в% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas.

 Корневым элементом является элемент [ProjectItem](../sharepoint/projectitem-element.md) . В следующей таблице описаны все элементы, определенные схемой.

|Элемент|Описание|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Представляет коллекцию пользовательских элементов данных, связанных с элементом проекта SharePoint.|
|[екстенсиондатаитем](../sharepoint/extensiondataitem-element.md)|Представляет пользовательский элемент данных, связанный с элементом проекта SharePoint, в формате "ключ — значение". Ключ и значение должны быть строками.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Представляет коллекцию значений свойств, включенных в компонент при развертывании в SharePoint. После развертывания компонента можно получить доступ к значениям свойств в коде.|
|[феатурепроперти](../sharepoint/featureproperty-element.md)|Представляет пользовательское свойство, которое входит в состав компонента при его развертывании в SharePoint. После развертывания компонента можно получить доступ к свойству в коде.|
|[Файлы](../sharepoint/files-element.md)|Указывает файлы для развертывания с помощью элемента проекта SharePoint, такие как файл элемента компонента или выходные данные проекта.|
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint.|
|[прожектитемфиле](../sharepoint/projectitemfile-element.md)|Представляет файл SharePoint, например файл элемента компонента, для включения в элемент проекта при его развертывании в SharePoint.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Представляет сопоставленную папку.|
|[прожектаутпутфиле](../sharepoint/projectoutputfile-element.md)|Представляет выходные данные проекта, включаемые в элемент проекта при его развертывании в SharePoint.|
|[SafeControl](../sharepoint/safecontrol-element.md)|Представляет элемент управления ASPX или веб-часть, которая обозначена как безопасная для доступа любого пользователя к любой странице ASPX на сайте SharePoint.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Представляет коллекцию элементов управления ASPX и веб-части, которые обозначены как безопасные для доступа любого пользователя к любой странице ASPX на сайте SharePoint.|

## <a name="see-also"></a>См. также раздел
- [Создание шаблонов элементов и проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
