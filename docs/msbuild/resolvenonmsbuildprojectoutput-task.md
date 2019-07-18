---
title: Задача ResolveNonMSBuildProjectOutput | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7060141f81054bf5daa27cdd09a07639be6e0ae8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996705"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput - задача
Определяет выходные файлы для ссылок на проекты, не относящихся к MSBuild.

## <a name="parameters"></a>Параметры
 В следующей таблице приводятся параметры задачи `ResolveNonMSBuildProjectOutput` .

|Параметр|Описание|
|---------------|-----------------|
|`PreresolvedProjectOutputs`|Необязательный параметр `String` .<br /><br /> Задает XML-строку, содержащую разрешенные выходные данные проекта.|
|`ProjectReferences`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Задает ссылки проекта.|
|`ResolvedOutputPaths`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит список путей разрешенных ссылок (и сохраняет исходные атрибуты ссылок проекта).|
|`UnresolvedProjectReferences`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит список элементов ссылок проекта, которые не удалось разрешить с помощью предварительно разрешенного списка выходных данных.<br /><br /> Так как Visual Studio предварительно разрешает только проекты, отличные от MSBuild, ссылки проекта в этом списке имеют формат MSBuild.|

## <a name="remarks"></a>Примечания
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)