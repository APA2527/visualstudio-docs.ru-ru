---
title: Элемент ProjectItemFolder | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 124716f8c40a8adc0a0ae1a28cda21dcb5e00ddf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562706"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder - элемент
  Представляет сопоставленную папку.

## <a name="syntax"></a>Синтаксис

```xml
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"
    Type = "Type of deployment for the mapped folder" />
```

## <a name="type"></a>Тип
 **ProjectItemFolderType**

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|**Целевой объект**|Требуется **xs: строка** атрибута.<br /><br /> Путь к папке в установке SharePoint, соответствующий сопоставленная папка, относительно корневой папки развертывания. Корневой папки развертывания определяется типом развертывания, заданные **тип** атрибута.<br /><br /> Дополнительные сведения см. в разделе описания **путь развертывания** и **Deployment Root** свойства SharePoint элементами проекта в среде [решения разработки SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Type**|Требуется **xs: String** атрибута.<br /><br /> Тип развертывания для сопоставленной папки. Дополнительные сведения о возможных значениях см. в описании для **тип развертывания** свойства элементов проекта SharePoint в [решения разработки SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint. Этот элемент является обязательным корневым элементом *.spdata* файла.|

## <a name="remarks"></a>Примечания
 Дополнительные сведения о сопоставленных папок см. в разделе [как: Добавление и удаление сопоставленных папок](../sharepoint/how-to-add-and-remove-mapped-folders.md).

## <a name="element-information"></a>Сведения об элементе

|||
|-|-|
|**Пространство имен**|http:\/\/schemas.microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|ProjectItemModelSchema.xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также
- [Справочник по схеме для элемента проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Практическое: Добавление и удаление сопоставленных папок](../sharepoint/how-to-add-and-remove-mapped-folders.md)
