---
title: Установка необходимых компонентов с помощью приложения ClickOnce
description: Узнайте, как выбрать необходимые компоненты для упаковки вместе с приложением ClickOnce при его установке.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09337ee164c8b740e9aa8a044c4a9df385f01016
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900564"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Практическое руководство. Установка необходимых компонентов для приложения ClickOnce
Для всех [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений требуется, чтобы на компьютере была установлена правильная версия платформа .NET Framework, прежде чем их можно будет запустить; у многих приложений также есть и другие необходимые компоненты. При публикации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения можно выбрать набор необходимых компонентов, которые будут упакованы вместе с приложением. Во время установки для каждого необходимого компонента будет выполнена проверка, чтобы определить, существует ли он уже. Если это не так, то оно будет установлено до установки [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения.

 Вместо того чтобы упаковывать и публиковать необходимые компоненты, можно также указать расположение для загрузки компонентов. Например, вместо включения предварительных требований для каждого опубликованного приложения можно использовать централизованную общую папку или расположение в Интернете, которое содержит установщики для всех необходимых компонентов — во время установки компоненты будут скачаны и установлены из этого расположения.

> [!IMPORTANT]
> Перед публикацией первого приложения необходимо добавить пакеты установщика необходимых компонентов на компьютер разработчика [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Дополнительные сведения см. [в разделе руководство. Включение необходимых компонентов в приложение ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).

 Предварительные требования управляются в диалоговом окне **необходимые компоненты** , доступном в области **Публикация** **конструктора проектов**.

> [!NOTE]
> В дополнение к предварительно определенному списку необходимых компонентов можно добавить в список собственные компоненты. Дополнительные сведения см. в разделе [Создание пакетов начального загрузчика](../deployment/creating-bootstrapper-packages.md).

### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Указание необходимых компонентов для установки с помощью приложения ClickOnce

1. Выбрав проект в **Обозреватель решений**, в меню **проект** выберите пункт **Свойства**.

2. Выберите панель **Публикация** .

3. Нажмите кнопку **Предварительные требования** , чтобы открыть диалоговое окно **необходимые компоненты** .

4. Убедитесь, что в диалоговом окне **Необходимые компоненты** установлен флажок **Создать программу установки для необходимых компонентов** .

5. В списке **необходимых** компонентов проверьте компоненты, которые необходимо установить, и нажмите кнопку **ОК**.

     Выбранные компоненты будут упакованы и опубликованы вместе с приложением.

### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Указание другого расположения загрузки для необходимых компонентов

1. Выбрав проект в **Обозреватель решений**, в меню **проект** выберите пункт **Свойства**.

2. Выберите панель **Публикация** .

3. Нажмите кнопку **Предварительные требования** , чтобы открыть диалоговое окно **необходимые компоненты** .

4. Убедитесь, что в диалоговом окне **Необходимые компоненты** установлен флажок **Создать программу установки для необходимых компонентов** .

5. В разделе **укажите расположение установки для необходимых компонентов** выберите **загрузить необходимые компоненты из следующего расположения**.

6. Выберите расположение из раскрывающегося списка или введите URL-адрес, путь к файлу или расположение FTP, а затем нажмите кнопку **ОК.**

    > [!NOTE]
    > Необходимо убедиться, что установщики для указанных компонентов существуют в указанном расположении.

## <a name="see-also"></a>См. также раздел
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)