---
title: Развертывание классического приложения Windows .NET с помощью ClickOnce
ms.date: 10/15/2020
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder, ClickOnce
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: john-hart
ms.author: JohnHart
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 5a6f7c2c8d6c79270df94c100bbd4625856efa15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934511"
---
# <a name="deploy-a-net-windows-desktop-application-using-clickonce"></a>Развертывание классического приложения Windows .NET с помощью ClickOnce

Начиная с Visual Studio 2019 версии 16.8 можно использовать средство **публикации** для публикации классических приложений Windows .NET Core 3.1 или более поздних версий с помощью ClickOnce из Visual Studio.

> [!NOTE]
> Если вам нужно опубликовать классическое приложение Windows .NET Framework, см. статью о [развертывании классического приложения с помощью ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# или Visual Basic).

## <a name="publishing-with-clickonce"></a>Публикация с помощью ClickOnce

1. В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать** (или воспользуйтесь командой меню **Сборка** > **Опубликовать**).

    ![Команда Опубликовать в контекстном меню проекта в обозревателе решений](../deployment/media/quickstart-clickonce-solution-explorer.png "Выбор команды Опубликовать")

1. Если ранее вы настроили какие-либо профили публикации, появится панель **Публикация**. Нажмите кнопку **Создать**.

1. В мастере **публикации** выберите **Папка**.

    ![Выбор папки в качестве целевого объекта публикации](../deployment/media/quickstart-clickonce-publish-folder-category.png "Выбор папки")

1. На странице **Указанный целевой объект** выберите **ClickOnce**.

    ![Выбор ClickOnce в качестве указанного целевого объекта](../deployment/media/quickstart-clickonce-publish-folder-target.png "Выбор ClickOnce")

1. Введите путь или выберите **Обзор**, чтобы выбрать расположение публикации.

    ![Указание пути к расположению публикации](../deployment/media/quickstart-clickonce-publish-location.png "Ввод пути")

1. На странице **Расположение установки** выберите место, куда пользователи будут устанавливать приложение.

    ![Указание пути к папке](../deployment/media/quickstart-clickonce-install-location.png "Выбор места установки")

1. На странице **Параметры** можно указать параметры, необходимые для ClickOnce.

1. Если выбрана установка из UNC-пути или с веб-сайта, на этой странице можно указать, будет ли приложение доступно в автономном режиме. Если этот параметр выбран, приложение будет указано в меню "Пуск" пользователей и будет автоматически обновляться при публикации новой версии. По умолчанию обновления доступны в папке установки.  Другое расположение для обновлений можно указать с помощью ссылки "Параметры обновления". Если вы не хотите, чтобы приложение было доступно в автономном режиме, оно будет запускаться из папки установки.

    ![Указание параметров публикации](../deployment/media/quickstart-clickonce-unc-settings.png "Выбор параметров публикации")

1. Если выбрана установка с компакт-диска, DVD-диска или USB-накопителя, на этой странице также можно указать, поддерживает ли приложение автоматические обновления. Если выбрана поддержка обновлений, требуется указать расположение обновления, которое должно быть допустимым UNC-путем или веб-сайтом.

    ![Выбор параметров публикации](../deployment/media/quickstart-clickonce-settings.png "Выбор параметров публикации")

С помощью ссылок в верхней части страницы можно указать, какие **файлы приложений** следует включить в программу установки, какие пакеты **необходимых компонентов** нужно установить, а также выбрать другие **параметры**.

Кроме того, на этой странице можно задать версию публикации и будет ли она автоматически увеличиваться при каждой публикации.

> [!NOTE]
> Номер версии публикации уникален для каждого профиля ClickOnce. Этот момент следует иметь в виду, если планируется использовать несколько профилей.

10. На странице **Подпись манифестов** можно указать, следует ли подписывать манифесты и какой сертификат нужно использовать.

    ![Подпись манифестов ClickOnce](../deployment/media/quickstart-clickonce-sign-manifests.png)

1. На странице **Конфигурация** можно выбрать нужную конфигурацию проекта.

     ![Указание конфигурации публикации](../deployment/media/quickstart-clickonce-configuration.png)

    Дополнительные сведения о выборе параметров см. в следующих статьях:

    - [Развертывание, зависящее от платформы, и автономное развертывание](/dotnet/core/deploying/)
    - [Идентификаторы целевой среды выполнения (переносной RID и т. п.)](/dotnet/core/rid-catalog)
    - [Конфигурации отладки и выпуска](../ide/understanding-build-configurations.md)

1. Щелкните **Готово**, чтобы сохранить новый профиль публикации ClickOnce.

1. На странице **Сводка** выберите **Опубликовать**, и Visual Studio создаст проект и опубликует его в указанную папку публикации. На этой странице также показана сводка профиля.

    ![Панель свойств публикации с обзором профиля](../deployment/media/quickstart-clickonce-summary.png)

1. Для повторной публикации выберите **Публиковать**.

## <a name="next-steps"></a>Следующие шаги

Для приложений .NET:

- [Развертывание .NET Framework и приложений](/dotnet/framework/deployment/)
- [Справочные сведения ClickOnce](clickonce-reference.md)
