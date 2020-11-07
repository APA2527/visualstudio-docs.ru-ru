---
title: Автоматическое обновление приложений с помощью API развертывания ClickOnce
description: Узнайте, как написать код в ClickOnce, использующий класс Аппликатиондеплоймент для проверки наличия обновлений на основе события, например запроса пользователя.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f00bd8aaa5db8ab72e6b6286763fd89fc900599f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351262"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Практическое руководство. Проверка обновлений для приложения программным способом с помощью развертывания API ClickOnce
Технология ClickOnce предоставляет два способа обновления приложения после его развертывания. В первом методе можно настроить развертывание ClickOnce для автоматической проверки обновлений через определенные промежутки времени. Во втором методе можно написать код, использующий <xref:System.Deployment.Application.ApplicationDeployment> класс для проверки наличия обновлений на основе события, например запроса пользователя.

 В следующих процедурах показан код для выполнения программного обновления, а также описывается настройка развертывания ClickOnce для включения программных проверок обновлений.

 Чтобы обновить приложение ClickOnce программным способом, необходимо указать расположение для обновлений. Иногда это называется поставщиком развертывания. Дополнительные сведения об установке этого свойства см. в разделе [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

> [!NOTE]
> Вы также можете использовать описанный ниже метод, чтобы развернуть приложение из одного расположения, но обновить его с другого. Дополнительные сведения см. [в разделе инструкции. Указание альтернативного расположения для обновлений развертывания](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).

### <a name="to-check-for-updates-programmatically"></a>Программная проверка обновлений

1. Создайте новое приложение Windows Forms с помощью предпочтительной командной строки или визуальных средств.

2. Создайте любую кнопку, пункт меню или другой элемент пользовательского интерфейса, который пользователи должны выбрать для проверки наличия обновлений. В обработчике событий этого элемента вызовите следующий метод, чтобы проверить наличие обновлений и установить их.

     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]

3. Скомпилируйте приложение.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Использование Mage.exe для развертывания приложения, которое программно проверяет на наличие обновлений

- Следуйте инструкциям по развертыванию приложения с помощью Mage.exe, как описано в [разделе Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). При вызове Mage.exe для создания манифеста развертывания обязательно используйте параметр командной строки `providerUrl` и укажите URL-адрес, по которому ClickOnce должен проверять наличие обновлений. Если приложение будет обновляться с `http://www.adatum.com/MyApp` , например, вызов для создания манифеста развертывания может выглядеть следующим образом:

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Использование MageUI.exe для развертывания приложения, которое программно проверяет на наличие обновлений

- Следуйте инструкциям по развертыванию приложения с помощью Mage.exe, как описано в [разделе Пошаговое руководство. Развертывание приложения ClickOnce вручную](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). На вкладке **Параметры развертывания** задайте для поля **начальное расположение** значение манифест приложения ClickOnce, которое должно проверять наличие обновлений. На вкладке **Параметры обновления** снимите флажок **это приложение должно проверять наличие обновлений** .

## <a name="net-framework-security"></a>Безопасность платформы .NET Framework
 Приложение должно иметь разрешения полного доверия для использования программного обновления.

## <a name="see-also"></a>См. также
- [Как указать альтернативное расположение для обновлений развертывания](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)