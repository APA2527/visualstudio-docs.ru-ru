---
title: Практическое руководство. Использование ссылки на имя или расположение файла проекта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eae8a32d4587b71f238c023d08a1328ce83ba37d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843005"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Практическое руководство. Использование ссылки на имя или расположение файла проекта
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Имя или расположение проекта в файле проекта можно использовать без создания отдельного свойства. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] предоставляет зарезервированные свойства, ссылающиеся на имя файла проекта, и другие свойства, связанные с проектом. Дополнительные сведения о зарезервированных свойствах см. в разделе [зарезервированные и стандартные свойства MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>Использование свойства MSBuildProjectName  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] предоставляет некоторые зарезервированные свойства, которые можно использовать в файлах проекта, не определяя их каждый раз. Например, зарезервированное свойство `MSBuildProjectName` предоставляет ссылку на имя файла проекта.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>Использование свойства MSBuildProjectName  
  
- Укажите ссылка на свойство в файле проекта с помощью нотации $() так же, как и для любого свойства. Пример:  
  
  ```  
  <CSC Sources = "@(CSFile)"   
      OutputAssembly = "$(MSBuildProjectName).exe"/>  
  </CSC>  
  ```  
  
  Преимущество использования зарезервированного свойства заключается в том, что любые изменения имени файла проекта применяются автоматически. В следующий раз при сборке проекта выходной файл будет иметь новое имя, и это не потребует никаких дополнительных действий с вашей стороны.  
  
> [!NOTE]
> Зарезервированные свойства нельзя переопределить в файле проекта.  
  
## <a name="example"></a>Пример  
 В следующем примере файл проекта ссылается на имя проекта как зарезервированное свойство, чтобы указать имя для выходных данных.  
  
```  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также:  
[MSBuild](msbuild.md)  
 [Зарезервированные и хорошо известные свойства MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
