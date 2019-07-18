---
title: Практическое руководство. Повторно подписать манифесты приложения и развертывания | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e934832f20ea7ab11484cdeb345f989aa842e06d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928356"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Практическое руководство. повторное подписание манифестов приложения и развертывания
После внесения изменений в свойства развертывания в манифесте приложения для приложений Windows Forms, приложения Windows Presentation Foundation (xbap) или решения Office, необходимо повторно подписать приложение и манифесты развертывания с помощью сертификат. Этот процесс позволяет проверить, не установлены ли на компьютер конечного пользователя измененные злоумышленниками файлы.

 Еще один сценарий, где могут заново подписывать манифесты, когда ваши заказчики хотят подписать приложение и манифесты развертывания своим собственным сертификатом.

## <a name="re-sign-the-application-and-deployment-manifests"></a>Повторное подписывание манифестов приложения и развертывания
 В этой процедуре предполагается, что вы уже внесены изменения в файле манифеста приложения (*.manifest*). Дополнительные сведения см. в разделе [Как Изменение свойств развертывания](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472).

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Для повторного подписания приложения и развертывания, манифестов с помощью Mage.exe

1. Откройте **Командная строка Visual Studio** окна.

2. Перейдите к папке, содержащей файлы, которые вы хотите войти.

3. Введите следующую команду, чтобы подписать файл манифеста приложения. Замените *ManifestFileName* на имя файла манифеста, а также добавляется расширение. Замените *сертификат* относительный или полный путь файла сертификата и замена *пароль* с паролем для сертификата.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Например вы выполните следующую команду, чтобы подписать манифест приложения для надстройки в приложении Windows Form и приложение браузера Windows Presentation Foundation. Временные сертификаты, созданные с помощью Visual Studio для развертывания в рабочих средах не рекомендуется.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. Введите следующую команду, чтобы обновить и подписать файл манифеста развертывания, заменив местозаполнители, как на предыдущем шаге.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Например можно выполнить следующую команду, чтобы обновить и подписать манифест развертывания для надстройки Excel, в приложении Windows Forms или приложение браузера Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. При необходимости скопировать основной манифест развертывания (*публикации\\\<имя_приложения > .application*) в каталог развертывания версии (*файлы publish\Application\\ \<имя_приложения > _\<версии >*).

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Обновление и повторное подписание манифестов приложения и развертывания
 В этой процедуре предполагается, что вы уже внесены изменения в файле манифеста приложения (*.manifest*), но существуют другие файлы, которые были обновлены. При обновлении файлов, необходимо также обновить хэш, который представляет файл.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Обновление и повторное подписание приложения и развертывания манифестов с помощью Mage.exe

1. Откройте **Командная строка Visual Studio** окна.

2. Перейдите к папке, содержащей файлы, которые вы хотите войти.

3. Удалить *.deploy* папку выходных данных расширение файла из файлов в публикации.

4. Введите следующую команду, чтобы обновить манифест приложения с новыми хэшами для обновленных файлов и подписать файл манифеста приложения. Замените *ManifestFileName* на имя файла манифеста, а также добавляется расширение. Замените *сертификат* относительный или полный путь файла сертификата и замена *пароль* с паролем для сертификата.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Например вы выполните следующую команду, чтобы подписать манифест приложения для надстройки в приложении Windows Form и приложение браузера Windows Presentation Foundation. Временные сертификаты, созданные с помощью Visual Studio для развертывания в рабочих средах не рекомендуется.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Введите следующую команду, чтобы обновить и подписать файл манифеста развертывания, заменив местозаполнители, как на предыдущем шаге.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Например можно выполнить следующую команду, чтобы обновить и подписать манифест развертывания для надстройки Excel, в приложении Windows Forms или приложение браузера Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. Добавить *.deploy* расширение файла обратно к файлам, за исключением того, файлы манифестов приложения и развертывания.

7. При необходимости скопировать основной манифест развертывания (*публикации\\\<имя_приложения > .application*) в каталог развертывания версии (*файлы publish\Application\\ \<имя_приложения > _\<версии >*).

## <a name="see-also"></a>См. также
- [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)
- [Управление доступом для кода для приложений ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce и технология Authenticode](../deployment/clickonce-and-authenticode.md)
- [Общие сведения о развертывании доверенных приложений](../deployment/trusted-application-deployment-overview.md)
- [Практическое руководство. Включить параметры безопасности ClickOnce-приложений](../deployment/how-to-enable-clickonce-security-settings.md)
- [Практическое руководство. Установка зоны безопасности для ClickOnce-приложения](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Практическое руководство. Установка пользовательских разрешений для ClickOnce-приложения](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Практическое руководство. Отладка ClickOnce-приложения с ограниченными разрешениями](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Практическое руководство. Добавление надежного издателя на клиентский компьютер для приложений ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Практическое руководство. Настройка поведения запроса о доверии ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)