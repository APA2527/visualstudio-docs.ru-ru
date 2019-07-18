---
title: '&lt;customErrorReporting&gt; элемент (развертывание ClickOnce) | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d42bd1f7304d9f50b6334d9ac8ddd4f626605d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900375"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt; элемент (развертывание ClickOnce)
Задает отображаемый в случае ошибки URI.

## <a name="syntax"></a>Синтаксис

```xml
<customErrorReporting
   uri
/>
```

## <a name="remarks"></a>Примечания
 Этот элемент является необязательным. Без него [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] отображает диалоговое окно ошибки, отображение стека исключений. Если `customErrorReporting` элемент присутствует, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] вместо отобразит этот URI, обозначается `uri` параметра. Универсальный код ресурса будет включить внешнее исключение класса, класс внутреннее исключение и сообщение внутреннего исключения в качестве параметров.

 Этот элемент используется для добавления функций создания отчетов в приложение. Поскольку сформированный URI включает сведения о типе ошибки, веб-сайт можно проанализировать эти сведения и отображения, например, об устранении.

## <a name="example"></a>Пример
 В следующем фрагменте представлен `customErrorReporting` элемента, сформированный URI может привести к его.

```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />

Example Generated Error:
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.
```

## <a name="see-also"></a>См. также
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)