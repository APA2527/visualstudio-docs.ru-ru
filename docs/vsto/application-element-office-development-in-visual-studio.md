---
title: '&lt;приложение&gt; элемент (Разработка решений Office в Visual Studio)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <application> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 80652f6752b87cf0413b0b3166b0cf3292231c25
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62942916"
---
# <a name="ltapplicationgt-element-office-development-in-visual-studio"></a>&lt;приложение&gt; элемент (Разработка решений Office в Visual Studio)
  Элемент `application` пространства имен `vstav3` служит оболочкой для описания решений Office. Дочерние элементы настроек уровня документа и надстроек VSTO отличаются друг от друга.

## <a name="syntax-for-document-level-customizations"></a>Синтаксис для настроек уровня документа

```xml
<application>
  <customization
    id
    <document
      solutionId
    />
  </customization>
</application>
```

## <a name="syntax-for-application-level-add-ins"></a>Синтаксис для надстроек уровня приложения

```xml
<application>
  <customization
    id
    <appAddin
      application
      loadBehavior
      keyName>
    <friendlyName></friendlyName>
    <description></description>
    <formRegions></formRegions>
  </customization>
</application>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `application` пространства имен `vstav3` — это узел, который включает все сведения о настройке, содержащиеся в пространстве имен `vstov4` .

 У элемента `application` нет атрибутов.

 Элемент `application` имеет следующий элемент.

### <a name="customization"></a>Настройка
 Роль `customization` элемент в `vstov3` пространство имен определяется в [ &#60;настройки&#62; элемент &#40;разработка решений Office в Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).

## <a name="document-level-customization-example"></a>Пример настройки на уровне документа

### <a name="description"></a>Описание
 В следующем примере кода показан элемент `application` в решении Office уровня документа, развернутом с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstav3:application>
  <vstov4:customizations
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
    <vstov4:customization>
      <vstov4:document
        solutionId="73e" />
    </vstov4:customization>
  </vstov4:customizations>
</vstav3:application>
```

## <a name="vsto-add-in-example"></a>Пример надстройки VSTO

### <a name="description"></a>Описание
 В следующем примере кода показан элемент `application` в решении Office уровня приложения, развернутом с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstav3:application>
  <vstov4:customizations
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
    <vstov4:customization>
      <vstov4:appAddIn
        application="Outlook"
        loadBehavior="3"
        keyName="ContosoOutlookAddIn">
        <vstov4:friendlyName>
          ContosoOutlookAddIn
        </vstov4:friendlyName>
        <vstov4:description>
          ContosoOutlookAddIn - Outlook VSTO Add-in
          created with Visual Studio Tools for Office
        </vstov4:description>
        <vstov4:formRegions>
          <vstov4:formRegion
              name="OutlookAddIn1.FormRegion1">
            <vstov4:messageClass name="IPM.Note" />
            <vstov4:messageClass name="IPM.Contact" />
            <vstov4:messageClass name="IPM.Appointment" />
          </vstov4:formRegion>
        </vstov4:formRegions>
      </vstov4:appAddIn>
    </vstov4:customization>
  </vstov4:customizations>
</vstav3:application>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)