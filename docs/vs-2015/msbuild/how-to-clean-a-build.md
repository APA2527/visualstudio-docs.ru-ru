---
title: Практическое руководство. Очистка сборки | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f8c64bb19d65540f8c72be9acb1c5f59deb3c8f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156640"
---
# <a name="how-to-clean-a-build"></a>Практическое руководство. Очистка построения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При очистке сборки все промежуточные и выходные файлы удаляются, а остаются только файлы проекта и компонентов. Из файлов проекта и компонентов можно собрать новые экземпляры промежуточных и выходных файлов. Библиотека общих задач, предоставляемая вместе с [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], включает в себя задачу [Exec](../msbuild/exec-task.md), позволяющую запускать системные команды. Дополнительные сведения о библиотеке задач см. в разделе [Справочник по задачам](../msbuild/msbuild-task-reference.md).  
  
## <a name="creating-a-directory-for-output-items"></a>Создание каталога для выходных элементов  
 По умолчанию файл EXE, создаваемый при компиляции проекта, помещается в один каталог с файлами проекта и исходными файлами. Однако чаще выходные элементы создаются в отдельном каталоге.  
  
#### <a name="to-create-a-directory-for-output-items"></a>Создание каталога для выходных элементов  
  
1. Используйте элемент `Property` для определения расположения и имени каталога. Например, создайте каталог с именем `BuiltApp` в каталоге, содержащем файлы проекта и исходные файлы:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2. Используйте задачу [MakeDir](../msbuild/makedir-task.md) для создания каталога, если он не существует. Пример:  
  
     `<MakeDir Directories = "$(builtdir)"`  
  
     `Condition = "!Exists('$(builtdir)')" />`  
  
## <a name="removing-the-output-items"></a>Удаление выходных элементов  
 Прежде чем создавать экземпляры промежуточных и выходных файлов, попробуйте очистить все предыдущие экземпляры промежуточных и выходных файлов. Используйте задачу [RemoveDir](../msbuild/removedir-task.md), чтобы удалить с диска каталог и все содержащиеся в нем файлы и каталоги.  
  
#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Удаление каталога и всех файлов в нем  
  
- Используйте задачу `RemoveDir`, чтобы удалить каталог. Пример:  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## <a name="example"></a>Пример  
 Приведенный ниже проект с примером кода содержит новый целевой объект `Clean`, который использует задачу `RemoveDir`, чтобы удалить каталог и все содержащиеся в нем файлы и каталоги. Также в этом примере целевой объект `Compile` создает отдельный каталог для выходных файлов, удаляемых при очистке сборки.  
  
 `Compile` определяется как целевой объект по умолчанию и используется автоматически, пока вы не укажете другой целевой объект или несколько таких объектов. Используйте параметр командной строки **/Target** , чтобы указать другой целевой объект. Пример:  
  
 `msbuild <file name>.proj /target:Clean`  
  
 Параметр **/Target** может быть сокращен до **/t** и может указывать более одного целевого объекта. Например, чтобы использовать целевой объект `Clean` и затем целевой объект `Compile`, введите:  
  
 `msbuild <file name>.proj /t:Clean;Compile`  
  
```  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <!-- Set the application name as a property -->  
        <name>HelloWorldCS</name>  
  
        <!-- Set the output folder as a property -->  
        <builtdir>BuiltApp</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <!-- Specify the inputs by type and file name -->  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Check whether an output folder exists and create  
        one if necessary -->  
        <MakeDir Directories = "$(builtdir)"   
            Condition = "!Exists('$(builtdir)')" />  
  
        <!-- Run the Visual C# compiler -->  
        <CSC Sources = "@(CSFile)"   
            OutputAssembly = "$(BuiltDir)\$(appname).exe">  
            <Output TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
  
    <Target Name = "Clean">  
        <RemoveDir Directories="$(builtdir)" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также:  
 [Задача Exec](../msbuild/exec-task.md)   
 [Задача MakeDir](../msbuild/makedir-task.md)   
 [Задача RemoveDir](../msbuild/removedir-task.md)   
 [Задача CSC](../msbuild/csc-task.md)   
 [Целевые объекты](../msbuild/msbuild-targets.md)
