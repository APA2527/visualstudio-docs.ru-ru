---
title: Практическое руководство. Проверка обновлений для приложения программным способом с помощью API развертывания ClickOnce | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c713b9e2fe78f8e9c499c1af5e60a21fd3aea13
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442160"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Практическое руководство. Проверка обновлений для приложения программным способом с помощью API развертывания ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce обеспечивает два способа обновления приложения после его развертывания. Во-первых можно настроить развертывание ClickOnce автоматически проверять наличие обновлений, через определенные промежутки времени. Во втором методе, можно написать код, использующий <xref:System.Deployment.Application.ApplicationDeployment> для проверки наличия обновлений на основе события, например запрос пользователя.  
  
 Следующие процедуры показан код для выполнения программного обновления, а также описывается настройка развертывания ClickOnce для обеспечения проверок программных обновлений.  
  
 Чтобы обновить приложение ClickOnce программно, необходимо указать расположение для обновления. Иногда это называется поставщик развертывания. Дополнительные сведения об установке данного свойства см. в разделе [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
> Можно также использовать метод, описанный ниже для развертывания приложения из одного расположения, но обновить ее из другого. Дополнительные сведения см. в разделе [Как Задание альтернативного местоположения для обновлений развертывания](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Чтобы проверить наличие обновлений программным способом  
  
1. Создайте новое приложение Windows Forms с помощью в предпочитаемое средство командной строки или визуального элемента.  
  
2. Создать любой кнопки, меню или другой элемент пользовательского интерфейса требуется пользователям выбирать проверить наличие обновлений. Из этого элемента в обработчик событий вызовите следующий метод для проверки и установки обновлений.  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3. Скомпилируйте приложение.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Развертывание приложения, которое проверяет наличие обновлений программным способом с помощью Mage.exe  
  
- Следуйте инструкциям по развертыванию приложения с помощью Mage.exe, как описано в [Пошаговое руководство: Развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). При вызове Mage.exe для создания манифеста развертывания, убедитесь, что для использования параметра командной строки `providerUrl`, а также указать URL-адрес, где приложение ClickOnce должно проверять наличие обновлений. Если приложение обновит из [ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp), например, при вызове создания манифеста развертывания может выглядеть следующим образом:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Развертывание приложения, которое проверяет наличие обновлений программным способом с помощью MageUI.exe  
  
- Следуйте инструкциям по развертыванию приложения с помощью Mage.exe, как описано в [Пошаговое руководство: Развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). На **варианты развертывания** вкладке **начальное расположение** поле в манифест приложения ClickOnce должно проверять наличие обновлений. На **параметры обновления** вкладке Очистить **это приложение должно проверять наличие обновлений** "флажок".  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Приложение должно иметь разрешения полного доверия для использования программного обновления.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Задание альтернативного местоположения для обновлений развертывания](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
