---
title: Задача ParallelCustomBuild | Документация Майкрософт
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.parallelcustombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 54623ab1c58d85de55c5b8a24384bf0be46f1a61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963758"
---
# <a name="parallelcustombuild-task"></a>Задача ParallelCustomBuild

Выполняет параллельные экземпляры [задачи CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Параметры

В следующей таблице описаны параметры задачи **ParallelCustomBuild**.

|Параметр|Описание|
|---------------|-----------------|
|**BreakOnFirstFailure**|Необязательный параметр типа **bool**.|
|**MaxItemsInBatch**|Необязательный параметр типа **int**.|
|**MaxProcesses**|Необязательный параметр типа **int**.|
|**Sources**|Обязательный параметр **ITaskItem[]**.|

## <a name="see-also"></a>См. также

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)