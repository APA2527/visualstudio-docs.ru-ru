---
title: '&lt;assemblyIdentity&gt; элемент (развертывание ClickOnce) | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56525cc0c0c754a7fa3a1f4c2c5b6cf2e941e9b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929058"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt; элемент (развертывание ClickOnce)
Определяет основную сборку из [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения.

## <a name="syntax"></a>Синтаксис

```xml

      <assemblyIdentity  
   name 
   version
   publicKeyToken
   processorArchitecture
    type
/>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 `assemblyIdentity` Элемент является обязательным. Он не содержит дочерних элементов и имеет следующие атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`name`|Обязательный. Определяет понятное имя развертывания в информационных целях.<br /><br /> Если `name` содержит специальные символы, такие как одинарные или двойные кавычки, приложение может вызвать сбой активации.|
|`version`|Обязательный. Указывает номер версии сборки, в следующем формате: `major.minor.build.revision`.<br /><br /> Обновленный манифест для активации обновления приложения необходимо увеличить это значение.|
|`publicKeyToken`|Обязательный. Задает 16-знаковая шестнадцатеричную строку, которая представляет последние 8 байтов хэша SHA-1 открытого ключа, которым подписаны манифеста развертывания. Открытый ключ, используемый для входа должно быть 2048 бит или более поздней версии.<br /><br /> Несмотря на то, что подпись сборки, рекомендуется, но необязательно, этот атрибут является обязательным. Если сборка не подписана, следует скопировать значение из собственной подписью сборки или использовать значение «пустого» все нули.|
|`processorArchitecture`|Обязательный. Указывает процессор. Допустимые значения: `msil` для всех процессоров `x86` для 32-разрядной Windows, `IA64` для 64-разрядной Windows, и `Itanium` для Intel 64-разрядных процессоров Itanium.|
|`type`|Обязательный. Для обеспечения совместимости с технологией side-by-side установки Windows. Единственное допустимое значение — `win32`.|

## <a name="remarks"></a>Примечания

## <a name="example"></a>Пример
 В следующем примере кода показано `assemblyIdentity` элемент [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест развертывания. Данный пример кода является частью большего примера для [манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) раздела.

```xml
<!-- Identify the deployment. -->
<assemblyIdentity
  name="My Application Deployment.app"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>См. также
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<assemblyIdentity > элемент](../deployment/assemblyidentity-element-clickonce-application.md)