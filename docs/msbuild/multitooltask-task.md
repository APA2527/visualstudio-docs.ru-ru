---
title: Задача MultiToolTask | Документация Майкрософт
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.multitooltask
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), MultiToolTask task
- MultiToolTask task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: a16a61c06bf80bef3fbb78f155cd8b41905a8d72
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963914"
---
# <a name="multitooltask-task"></a>Задача MultiToolTask

Нет описания.

## <a name="parameters"></a>Параметры

В представленной ниже таблице приводятся параметры задачи **MultiToolTask**.

|Параметр|Описание|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|Необязательный параметр типа **string[]**.|
|**SemaphoreProcCount**|Необязательный параметр типа **string**.|
|**SchedulerFunction**|Необязательный параметр типа **string**.|
|**SchedulerVerbose**|Необязательный параметр типа **bool**.|
|**Sources**|Обязательный параметр **ITaskItem[]**.|
|**TaskAssemblyName**|Необязательный параметр типа **string**.|
|**TaskName**|Обязательный параметр **string**.|
|**TrackerLogDirectory**|Обязательный параметр **string**.|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)