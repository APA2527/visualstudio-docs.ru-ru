---
title: Задача SignFile | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 08db6a5d22cacc348a9ef36fd9e9857d5b55642a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703726"
---
# <a name="signfile-task"></a>Задача SignFile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Подписывает указанный файл с помощью заданного сертификата.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `SignFile` .  
  
 Обратите внимание, что сертификаты SHA-256 разрешены только на компьютерах с .NET 4.5 или более поздней версией.  
  
> [!WARNING]
> Начиная с Visual Studio 2013 с обновлением 3, для этой задачи используется новая подпись, которая позволяет указывать версию целевой платформы для файла. Новую подпись рекомендуется использовать там, где это возможно, поскольку процесс MSBuild работает с хэшами SHA-256 только в том случае, если поддерживается целевая платформа .NET 4.5 или более поздней версии. Если версия целевой платформы .NET 4.0 или ниже, хэш SHA-256 использоваться не будет.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`CertificateThumbprint`|Обязательный параметр `String` .<br /><br /> Задает сертификат, который будет использоваться для подписи. Этот сертификат должен находиться в личном хранилище текущего пользователя.|  
|`SigningTarget`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Задает файлы, который будут подписаны с помощью сертификата.|  
|`TimestampUrl`|Необязательный параметр `String` .<br /><br /> Задает URL-адрес сервера отметок времени.|  
|`TargetFrameworkVersion`|Версия платформы .NET Framework, используемой для целевого объекта.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров эта задача наследует параметры от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Task Base Class](../msbuild/task-base-class.md) (Базовый класс Task).  
  
## <a name="example"></a>Пример  
 В следующем примере используется задача `SignFile` для подписания файлов, указанных в коллекции элементов `FilesToSign`, с помощью сертификата, заданного свойством `Certificate`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.exe" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.5" />  
    </Target>  
</Project>  
```  
  
> [!NOTE]
> Отпечатком сертификата является хэш SHA-1 сертификата. Дополнительные сведения см. в разделе [Получение хэша SHA-1 сертификата доверенного корневого ЦС](https://msdn.microsoft.com/dd641990-9a88-4228-a245-017797131a87).  
  
## <a name="example"></a>Пример  
 В следующем примере используется задача `Exec` для подписания файлов, указанных в коллекции элементов `FilesToSign`, с помощью сертификата, заданного свойством `Certificate`. Этот пример можно использовать для подписи файлов установщика Windows во время процесса построения.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.msi" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <Exec Command="signtool.exe sign /f CertFile /p Password "@(FileToSign)" "/>  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.0" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)
