---
title: Задача UnregisterAssembly | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f8cddcf9bf0632914d1a6de1cc904dbf0f173e6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631501"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly - задача

Отменяет регистрацию указанных сборок для целей COM-взаимодействия. Эта задача противоположна [задаче RegisterAssembly](../msbuild/registerassembly-task.md).

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `UnregisterAssembly`.

|Параметр|Description|
|---------------|-----------------|
|`Assemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает сборки, регистрацию которых следует отменить.|
|`AssemblyListFile`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Содержит сведения о состоянии взаимодействия между задачами `RegisterAssembly` и `UnregisterAssembly`. Благодаря этому задача не пытается отменить регистрацию для сборки, которую не удалось зарегистрировать в задаче `RegisterAssembly`.<br /><br /> Если этот параметр указан, параметры `Assemblies` и `TypeLibFiles` игнорируются.|
|`TypeLibFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Отменяет регистрацию библиотеки заданного типа в указанной сборке. **Примечание.** Этот параметр является обязательным только в том случае, если имя файла библиотеки типов отличается от имени сборки.|

## <a name="remarks"></a>Remarks

 Для успешного выполнения задачи не требуется, чтобы существовала указанная сборка. Если вы попытаетесь отменить регистрацию несуществующей сборки, задача завершится успешно с предупреждением. Такая логика объясняется тем, что целью этой задачи является удаление регистрации сборки из реестра. Если сборка не существует, то в реестре нет информации о ней, следовательно, задача выполнена успешно.

 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension>, который, в свою очередь, наследует от класса <xref:System.MarshalByRefObject>. Класс `MarshalByRefObject` предоставляет те же возможности, что и класс <xref:Microsoft.Build.Utilities.Task>, но его экземпляр можно создать в собственном домене приложения.

## <a name="example"></a>Пример

 В следующем примере задача `UnregisterAssembly` отменяет регистрацию сборки, расположенной по пути, указанному в свойствах `OutputPath` и `FileName`, если такая сборка существует.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <OutputPath>\Output\</OutputPath>
        <FileName>MyFile.dll</FileName>
    </PropertyGroup>
    <Target Name="UnregisterAssemblies">
        <UnregisterAssembly
            Condition="Exists('$(OutputPath)$(FileName)')"
            Assemblies="$(OutputPath)$(FileName)" />
    </Target>

</Project>
```

## <a name="see-also"></a>См. также раздел

- [Задача RegisterAssembly](../msbuild/registerassembly-task.md)
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)