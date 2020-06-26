---
title: Развертывание приложений для различных версий с помощью ClickOnce
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7ede1cb4faa437d9cff8bd1239f9c271112ccf72
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381708"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Практическое руководство. Использование технологии ClickOnce для развертывания приложений, которые могут выполняться в нескольких версиях .NET Framework
Приложение, предназначенное для нескольких версий .NET Framework, можно развернуть с помощью технологии развертывания ClickOnce. Для этого необходимо создать и обновить манифесты приложения и развертывания.

> [!NOTE]
> Перед изменением приложения для использования нескольких версий .NET Framework следует убедиться, что приложение работает с несколькими версиями .NET Framework. Версия среды CLR отличается от .NET Framework 4 до .NET Framework 2,0, .NET Framework 3,0 и .NET Framework 3,5.

 Этот процесс требует выполнения следующих действий.

1. Создание манифестов приложения и развертывания.

2. Измените манифест развертывания, чтобы получить список нескольких .NET Framework версий.

3. Измените файл *app.config* , чтобы получить список совместимых версий среды выполнения .NET Framework.

4. Измените манифест приложения, чтобы пометить зависимые сборки как сборки .NET Framework.

5. Подпишите манифест приложения.

6. Обновите и подпишите манифест развертывания.

### <a name="to-generate-the-application-and-deployment-manifests"></a>Создание манифестов приложения и развертывания

- Используйте мастер публикации или страницу Публикация в конструкторе проектов, чтобы опубликовать приложение и создать файлы манифеста приложения и развертывания. Дополнительные сведения см. в разделе [инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) или [страницы публикации конструктора проектов](../ide/reference/publish-page-project-designer.md).

### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Изменение манифеста развертывания для перечисления нескольких .NET Framework версий

1. В каталоге публикации откройте манифест развертывания с помощью редактора XML в Visual Studio. Манифест развертывания имеет расширение имени файла *приложения* .

2. Замените XML-код между `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` элементами и `</compatibleFrameworks>` XML-кодом, который содержит список поддерживаемых версий .NET Framework для приложения.

     В следующей таблице показаны некоторые из доступных версий .NET Framework и соответствующий XML-код, который можно добавить в манифест развертывания.

    |Версия платформы .NET Framework|XML|
    |----------------------------|---------|
    |4 Client|\<framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />|
    |4 Full|\<framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />|
    |3.5 Client|\<framework targetVersion="3.5" profile="Client" supportedRuntime="2.0.50727" />|
    |3.5 Full|\<framework targetVersion="3.5" profile="Full" supportedRuntime="2.0.50727" />|
    |3.0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|

### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Изменение файла app.config для вывода списка совместимых версий среды выполнения .NET Framework

1. В обозреватель решений откройте файл *app.config* с помощью редактора XML в Visual Studio.

2. Замените (или добавьте) XML-код между `<startup>` элементами и `</startup>` с XML, в котором перечислены поддерживаемые среды выполнения .NET Framework для вашего приложения.

     В следующей таблице показаны некоторые из доступных версий .NET Framework и соответствующий XML-код, который можно добавить в манифест развертывания.

    |Версия среды выполнения .NET Framework|XML|
    |------------------------------------|---------|
    |4 Client|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0,Profile=Client" />|
    |4 Full|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0" />|
    |3.5 Full|\<supportedRuntime version="v2.0.50727"/>|
    |3.5 Client|\<supportedRuntime version="v2.0.50727" sku="Client"/>|

### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Изменение манифеста приложения для пометки зависимых сборок в качестве .NET Frameworkных сборок

1. В каталоге публикации откройте манифест приложения с помощью редактора XML в Visual Studio. Манифест развертывания имеет расширение имени файла *manifest* .

2. Добавьте `group="framework"` в XML-файл зависимости для сборок Sentinel ( `System.Core` , `WindowsBase` , `Sentinel.v3.5Client` и `System.Data.Entity` ). Например, XML должен выглядеть следующим образом:

   ```xml
   <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">
   ```

3. Измените номер версии `<assemblyIdentity>` элемента для Microsoft. Windows. коммонлангуажерунтиме на номер версии для .NET Framework, который является наименьшим общим знаменателем. Например, если приложение предназначено для .NET Framework 3,5 и .NET Framework 4, используйте номер версии 2.0.50727.0 и XML-код должен выглядеть следующим образом:

   ```xml
   <dependency>
     <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
       <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />
     </dependentAssembly>
   </dependency>
   ```

### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Обновление и повторное подписание манифестов приложения и развертывания

- Обновите и повторно подпишите манифесты приложения и развертывания. Дополнительные сведения см. [в разделе как повторно подписывать манифесты приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>См. также
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [\<compatibleFrameworks>дерев](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [\<dependency>дерев](../deployment/dependency-element-clickonce-application.md)
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Схема файла конфигурации](/dotnet/framework/configure-apps/file-schema/index)
