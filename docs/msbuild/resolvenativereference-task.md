---
title: Задача ResolveNativeReference | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 417c4536f13aa90505ec5e69b2719219af0d7e81
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595167"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference - задача
Разрешает машинные ссылки. Реализует класс <xref:Microsoft.Build.Tasks.ResolveNativeReference>. Этот класс поддерживает инфраструктуру .NET Framework, которая не предназначена для использования непосредственно из программного кода.

## <a name="task-parameters"></a>Параметры задачи
 В следующей таблице приводятся параметры задачи `ResolveNativeReference` .

|Параметр|Описание|
|---------------|-----------------|
|`AdditionalSearchPaths`|Обязательный параметр <xref:System.String?displayProperty=fullName>`[]`.<br /><br /> Получает или задает пути поиска для разрешения идентификаторов сборок для собственных ссылок.|
|`ContainedComComponents`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Получает или задает компоненты COM машинной сборки.|
|`ContainedLooseEtcFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Возвращает или задает свободные *ETC-файлы*, перечисленные в собственном манифесте.|
|`ContainedLooseTlbFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Получает или задает свободные *TLB-файлы* машинной сборки.|
|`ContainedPrerequisiteAssemblies`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Получает или задает сборки, которые должны быть созданы до использования манифеста.|
|`ContainedTypeLibraries`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Получает или задает библиотеки типов машинной сборки.|
|`ContainingReferenceFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Получает или задает файлы ссылок.|
|`NativeReferences`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Получает или задает ссылки на сборки в машинном коде Win32.|

## <a name="remarks"></a>Примечания
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
