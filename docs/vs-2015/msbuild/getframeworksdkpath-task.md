---
title: Задача GetFrameworkSdkPath | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e6d527b00e8cbfe6a6f4ad5d112a23e46d4edb8e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149559"
---
# <a name="getframeworksdkpath-task"></a>Задача GetFrameworkSdkPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Извлекает путь к [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `GetFrameworkSdkPath`.  
  
|Параметр|ОПИСАНИЕ|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Необязательный выходной параметр `String`, доступный только для чтения.<br /><br /> Возвращает путь к пакету SDK для .NET версии 2.0 при его наличии. В противном случае возвращает значение `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Необязательный выходной параметр `String`, доступный только для чтения.<br /><br /> Возвращает путь к пакету SDK для .NET версии 3.5 при его наличии. В противном случае возвращает значение `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Необязательный выходной параметр `String`, доступный только для чтения.<br /><br /> Возвращает путь к пакету SDK для .NET версии 4.0 при его наличии. В противном случае возвращает значение `String.Empty`.|  
|`Path`|Необязательный выходной параметр `String`.<br /><br /> Содержит путь к последнему пакету SDK для .NET при любой из его версий. В противном случае возвращает значение `String.Empty`.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 Следующий пример использует задачу `GetFrameworkSdkPath` для сохранения пути к [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] в свойстве `SdkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
