---
title: Задача Touch | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Touch
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Touch task
- Touch task [MSBuild]
ms.assetid: 8a978645-1393-4904-ae69-42afabd8c109
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf68bf5dada310a23136e431fdaecad3e738d4bc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68144270"
---
# <a name="touch-task"></a>Задача Touch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Задает время доступа и изменения файлов.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `Touch` .  
  
|Параметр|ОПИСАНИЕ|  
|---------------|-----------------|  
|`AlwaysCreate`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, создаются файлы, которые еще не существуют.|  
|`Files`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Определяет коллекцию файлов для изменения.|  
|`ForceTouch`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, вызывает принудительное изменение файлов, даже если они доступны только для чтения.|  
|`Time`|Необязательный параметр `String` .<br /><br /> Задает время, отличное от текущего. Формат должен быть допустимым для метода <xref:System.DateTime.Parse%2A>.|  
|`TouchedFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит коллекцию успешно измененных элементов.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В следующем примере используется задача `Touch` для изменения времени доступа и изменения файлов, указанных в элементе `Files` коллекции с последующим размещением списка успешно измененных файлов в коллекцию элементов `FilesTouched`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
<ItemGroup>  
    <Files Include="File1.cs;File2.cs;File3.cs" />  
</ItemGroup>  
  
    <Target Name="TouchFiles">  
        <Touch  
            Files="@(Files)">  
            <Output  
                TaskParameter="TouchedFiles"  
                ItemName="FilesTouched"/>  
    </Touch>  
</Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
