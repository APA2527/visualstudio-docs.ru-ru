---
title: '&lt;&gt;элемент compatibleFrameworks (развертывание ClickOnce) | Документация Майкрософт'
description: Элемент compatibleFrameworks определяет версии платформа .NET Framework, в которых можно установить и запустить это приложение.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6b0a87e36a176a01b8f243c4646e2711220f807f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881182"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;&gt;элемент compatibleFrameworks (развертывание ClickOnce)
Идентифицирует версии платформы .NET Framework, где можно установить и выполнять это приложение.

> [!NOTE]
> [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) не поддерживает `compatibleFrameworks` элемент при сохранении манифеста приложения, который уже подписан с помощью сертификата, использующего [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Вместо этого необходимо использовать [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="syntax"></a>Синтаксис

```xml
<compatibleFrameworks
      SupportUrl> 
   <framework
      targetVersion
      profile
      supportedRuntime
   /> 
</ compatibleFrameworks>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 `compatibleFrameworks`Элемент необходим для манифестов развертывания, предназначенных для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] среды выполнения, предоставляемой платформа .NET Framework 4 или более поздней версии. `compatibleFrameworks`Элемент содержит один или несколько `framework` элементов, указывающих версии платформа .NET Framework, в которых может выполняться это приложение. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Среда выполнения запустит приложение в первом доступном `framework` списке.

 В следующей таблице перечислены атрибуты, `compatibleFrameworks` поддерживаемые элементом.

|Атрибут|Описание|
|---------------|-----------------|
|`S` `upportUrl`|Необязательный элемент. Указывает URL-адрес, по которому может быть скачана предпочтительная совместимая версия платформа .NET Framework.|

## <a name="framework"></a>платформа
 Обязательный элемент. В следующей таблице перечислены атрибуты, которые `framework` поддерживает элемент.

|Атрибут|Описание|
|---------------|-----------------|
|`targetVersion`|Обязательный элемент. Указывает номер версии целевого платформа .NET Framework.|
|`profile`|Обязательный элемент. Указывает профиль целевого платформа .NET Framework.|
|`supportedRuntime`|Обязательный элемент. Указывает номер версии среды выполнения, связанной с целевым платформа .NET Framework.|

## <a name="remarks"></a>Remarks

## <a name="example"></a>Пример
 В следующем примере кода показан `compatibleFrameworks` элемент в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифесте развертывания. Это развертывание может выполняться на [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] . Он также может выполняться на платформа .NET Framework 4, так как он является надмножеством [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] .

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>См. также раздел
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)