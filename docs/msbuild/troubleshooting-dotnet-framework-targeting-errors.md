---
title: Устранение неполадок, связанных с нацеливанием платформы .NET Framework | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 041a04827ee904f309b62b8fb875198cc8991b34
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434157"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>Устранение неполадок, связанных с настройкой для определенных версий платформы .NET Framework
В этом разделе описаны ошибки MSBuild, которые могут возникнуть из-за проблем со ссылками, и методы устранения этих ошибок.

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Используется ссылка на проект или сборку, которая нацелена на другую версию .NET Framework
 Вы можете использовать в приложениях ссылки на проекты или сборки, нацеленные на другие версии платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Например, можно создать приложение для работы с клиентскими профилями [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)], которое ссылается на сборку, нацеленную на версию .NET Framework 2.0. Но если вы создаете проект, нацеленный на более раннюю версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], в нем нельзя использовать ссылки на проекты или сборки, нацеленные на клиентский профиль для [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] или [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]. Чтобы устранить эту ошибку, ваше приложение должно быть нацелено на профили, которые совместимы с профилями, для работы с которыми предназначены проекты или сборки, на которые, в свою очередь, ссылается ваше приложение.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Проект перенацелен на другую версию платформы .NET Framework
 Когда вы изменяете для приложения целевую версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio изменяет некоторые ссылки, но остальные нужно обновить вручную. Например, одна из указанных выше ошибок может возникать при перенацеливании приложения на [!INCLUDE[net_v35SP1_long](../msbuild/includes/net_v35sp1_long_md.md)], если это приложение использует ресурсы или параметры, основанные на клиентских профилях для [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)].

 Чтобы решить проблему с настройками приложения, откройте **обозреватель решений**, выберите **Показать все файлы**, а затем измените файл *app.config* в XML-редакторе Visual Studio. Установите здесь в параметрах соответствующую версию платформы .NET Framework. Например, вы можете изменить значение версии с 4.0.0.0 на 2.0.0.0. Аналогичным образом для приложения с добавленными ресурсами откройте **обозреватель решений**, нажмите кнопку **Показать все файлы**, затем разверните **Мой проект** (Visual Basic) или **Свойства** (C#) и измените файл *Resources.resx* в XML-редакторе Visual Studio. Замените здесь значение версии с 4.0.0.0 на 2.0.0.0.

 Если приложение содержит ресурсы (например, значки или растровые изображения) или параметры (например, строки подключения к данным), для устранения этой ошибки удалите все элементы на странице **Параметры** в **конструкторе проектов**, а затем заново добавьте все необходимые настройки.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Проект перенацелен на другую версию платформы .NET Framework, а ссылки не разрешаются
 Если вы перенацеливаете проект на другую версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], ссылки в некоторых случаях не будут правильно разрешаться. Чаще всего эта проблема связана с использованием полных ссылок на сборки. Для ее устранения можно удалить все ссылки, которые не могут разрешиться, и добавить их в проект заново. Также вы можете вручную изменить ссылки в файле проекта. Прежде всего следует удалить все ссылки, которые имеют такую форму:

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 Затем их нужно заменить ссылками в простой форме:

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> После этого закройте проект, повторно откройте и перестройте его, чтобы все ссылки наверняка разрешились правильно.

## <a name="see-also"></a>См. также
- [Практическое руководство. Определение целевой версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)
- [.NET Framework (клиентский профиль)](/dotnet/framework/deployment/client-profile)
- [Настройка конкретной целевой версии платформы .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md)