---
title: Задача ConvertToAbsolutePath | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ConvertToAbsolutePath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ConvertToAbsolutePath task [MSBuild]
- MSBuild, ConvertToAbsolutePath task
ms.assetid: f1af2cb8-b4ef-4a72-be80-22fa526c4491
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e37c57119f74b9ab5f3157c6b88f9405799a2e82
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596103"
---
# <a name="converttoabsolutepath-task"></a>ConvertToAbsolutePath - задача
Преобразует относительный путь или ссылку в абсолютный путь.

## <a name="task-parameters"></a>Параметры задачи
 В следующей таблице приводятся параметры задачи `ConvertToAbsolutePath` .

|Параметр|Описание|
|---------------|-----------------|
|`Paths`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Список относительных путей, подлежащих преобразованию в абсолютные пути.|
|`AbsolutePaths`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Список абсолютных путей для переданных элементов.|

## <a name="remarks"></a>Примечания
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
