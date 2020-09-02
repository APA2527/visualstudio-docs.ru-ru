---
title: Как опубликовать проект с определенной национальной настройкой | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, localized projects
- locales, publishing for
- deploying applications [ClickOnce], localized projects
- locales, deploying for
- publishing localized projects
- macros, deploying with
- macros, publishing with
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 42fc6e45e0e32e9b165251c7ec61d3d67b924e1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697609"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Практическое руководство. Публикация проекта, имеющего конкретный языковый стандарт
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Приложения нередко содержат компоненты с разными языковыми стандартами. В данном сценарии вы создадите решение, включающее несколько проектов, а затем опубликуете отдельные проекты для каждого языкового стандарта. Эта процедура показывает, как использовать макрос для публикации первого проекта в решении, на примере языкового стандарта "en". Если вы хотите выполнить данную процедуру с другим языковым стандартом, выберите в макросе соответствующее значение `localeString` (например, "de" или "de-DE").  
  
> [!NOTE]
> При использовании данного макроса расположение публикации должно быть выражено действительным URL-адресом или UNC-путем к общей папке. Также на компьютере должны быть установлены службы IIS. Чтобы установить службы IIS, в меню **Пуск** выберите **Панель управления**. Дважды щелкните пункт **Установка и удаление программ**. В окне **Установка и удаление программ** щелкните **Добавить/удалить компоненты Windows**. В **Мастере компонентов Windows** установите флажок **Службы IIS** в списке **Компоненты**. Затем нажмите **Готово**, чтобы закрыть мастер.  
  
### <a name="to-create-the-publishing-macro"></a>Создание макроса публикации  
  
1. Чтобы открыть обозреватель макросов, в меню **Сервис** наведите указатель мыши на параметр **Макрос** и выберите пункт **Обозреватель макросов**.  
  
2. Создайте макромодуль. В обозревателе макросов выберите **MyMacros**. В меню **Сервис** наведите указатель мыши на параметр **Макрос** и выберите пункт **Создать макромодуль**. Присвойте модулю имя **PublishSpecificCulture**.  
  
3. В обозревателе макросов разверните узел **MyMacros** и дважды щелкните модуль **PublishAllProjects** (либо в меню **Сервис** наведите указатель мыши на параметр **Макрос** и выберите пункт **Интегрированная среда разработки макросов**).  
  
4. В интегрированной среде разработки макросов добавьте в модуль следующий код после операторов `Import`:  
  
    ```vb  
    Module PublishSpecificCulture  
        Sub PublishProjectFirstProjectWithEnLocale()  
            ' Note: You should publish projects by using the IDE at least once  
            ' before you use this macro. Items such as the certificate and the   
            ' security zone must be set.  
            Dim localeString As String = "en"  
  
            ' Get first project.  
            Dim proj As Project = DTE.Solution.Projects.Item(1)  
            Dim publishProperties As Object = proj.Properties.Item("Publish").Value  
  
            ' GenerateManifests and SignManifests must always be set to  
            ' True for publishing to work.   
            proj.Properties.Item("GenerateManifests").Value = True  
            proj.Properties.Item("SignManifests").Value = True  
  
            'Set the publish language.  
            'This will set the deployment language and pick up all   
            ' en resource dlls:  
            Dim originalTargetCulture As String = _  
                publishProperties.Item("TargetCulture").Value  
            publishProperties.Item("TargetCulture").Value = localeString  
  
            'Append 'en' to end of publish, install, and update URLs if needed:  
            Dim originalPublishUrl As String = _  
                publishProperties.Item("PublishUrl").Value  
            Dim originalInstallUrl As String = _  
                publishProperties.Item("InstallUrl").Value  
            Dim originalUpdateUrl As String = _  
                publishProperties.Item("UpdateUrl").Value  
            publishProperties.Item("PublishUrl").Value = _  
                AppendStringToUrl(localeString, New Uri(originalPublishUrl))  
            If originalInstallUrl <> String.Empty Then  
                publishProperties.Item("InstallUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalInstallUrl))  
            End If  
            If originalUpdateUrl <> String.Empty Then  
                publishProperties.Item("UpdateUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalUpdateUrl))  
            End If  
            proj.Save()  
  
            Dim slnbld2 As SolutionBuild2 = _  
                CType(DTE.Solution.SolutionBuild, SolutionBuild2)  
            slnbld2.Clean(True)  
  
            slnbld2.BuildProject( _  
            proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
            proj.UniqueName, True)  
  
            ' Only publish if build is successful.  
            If slnbld2.LastBuildInfo <> 0 Then  
                MsgBox("Build failed for " & proj.UniqueName)  
            Else  
                slnbld2.PublishProject( _  
                proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
                proj.UniqueName, True)  
                If slnbld2.LastPublishInfo = 0 Then  
                    MsgBox("Publish succeeded for " & proj.UniqueName _  
                    & vbCrLf & "." _  
                    & " Publish Language was '" & localeString & "'.")  
                Else  
                    MsgBox("Publish failed for " & proj.UniqueName)  
                End If  
            End If  
  
            ' Return URLs and target culture to their previous state.  
            publishProperties.Item("PublishUrl").Value = originalPublishUrl  
            publishProperties.Item("InstallUrl").Value = originalInstallUrl  
            publishProperties.Item("UpdateUrl").Value = originalUpdateUrl  
            publishProperties.Item("TargetCulture").Value = originalTargetCulture  
            proj.Save()  
        End Sub  
  
        Private Function AppendStringToUrl(ByVal str As String, _  
        ByVal baseUri As Uri) As String  
            Dim returnValue As String = baseUri.OriginalString  
            If baseUri.IsFile OrElse baseUri.IsUnc Then  
                returnValue = IO.Path.Combine(baseUri.OriginalString, str)  
            Else  
                If Not baseUri.ToString.EndsWith("/") Then  
                    returnValue = baseUri.OriginalString & "/" & str  
                Else  
                    returnValue = baseUri.OriginalString & str  
                End If  
            End If  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
5. Закройте интегрированную среду разработки макросов. После этого вы вернетесь в Visual Studio.  
  
### <a name="to-publish-a-project-for-a-specific-locale"></a>Публикация проекта для отдельного языкового стандарта  
  
1. Чтобы создать проект приложения Windows в Visual Basic, в меню **Файл** наведите указатель мыши на параметр **Создать** и выберите пункт **Проект**.  
  
2. В диалоговом окне **Создать проект** выберите **Приложение Windows** в узле **Visual Basic**. Назовите проект **PublishLocales**.  
  
3. Откройте форму 1. В окне **Свойства** в разделе **Разработка** измените свойство **Язык** со значения **(По умолчанию)** на **Английский**. Измените свойство **Текст** формы на **MyForm**.  
  
     Обратите внимание, что локализованные источники DLL не создаются, пока в них возникает необходимость. Например, они создаются в случае изменении текста формы или одного из элементов управления после того, как будет указан новый языковой стандарт.  
  
4. Опубликуйте проект PublishLocales через интегрированную среду разработки Visual Studio.  
  
     В **Обозреватель решений**выберите публишлокалес. В меню **Проект** выберите пункт **Свойства**. В конструкторе проектов на странице **Публикация** укажите расположение публикации **http://localhost/PublishLocales** и нажмите кнопку **Опубликовать сейчас**.  
  
     Когда откроется веб-страница публикации, закройте ее. (Для этого шага необходимо только опубликовать проект, установка не требуется.)  
  
5. Опубликуйте проект PublishLocales еще раз, вызвав макрос в окне командной строки Visual Studio. Чтобы открыть окно командной строки, в меню **вид** выберите пункт **другие окна** , а затем пункт **командное окно**или нажмите клавиши CTRL + ALT + A. В окне командной строки введите `macros` ; Автозаполнение предоставит список доступных макросов. Выберите следующий макрос и нажмите клавишу ВВОД:  
  
     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`  
  
6. Если процесс публикации завершен успешно, появится сообщение "Публикация макроса PublishLocales\PublishLocales.vbproj успешно завершена. Язык публикации — EN. " В окне сообщения нажмите кнопку **ОК** . Когда откроется веб-страница публикации, нажмите кнопку **Установить**.  
  
7. Перейдите в папку C:\Inetpub\wwwroot\PublishLocales\en. Она должна содержать установленные файлы, такие как манифесты, setup.exe и файл публикации веб страницы, а также локализованный источник DLL. (По умолчанию ClickOnce присваивает файлам .EXE и .DLL расширение .DEPLOY, которое после развертывания можно удалить.)  
  
## <a name="see-also"></a>См. также:  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Среда разработки макросов](https://msdn.microsoft.com/d23105d8-34fe-4ad9-8278-fae2c660aeac)   
 [Окно обозревателя макросов](https://msdn.microsoft.com/762169e6-f83f-44b4-bffa-d0f107cae9a3)   
 [Руководство. Редактирование и программное создание макросов](https://msdn.microsoft.com/6716f820-1feb-48ad-a718-27eb6b473c5a)
