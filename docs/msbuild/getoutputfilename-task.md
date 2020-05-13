---
title: Задача GetOutputFileName | Документация Майкрософт
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutputfilename
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d66a7be3751e74ff75787ef194f90da1dcd1d3ce
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593295"
---
# <a name="getoutputfilename-task"></a>Задача GetOutputFileName

Задача вспомогательного приложения для извлечения имени выходного файла для cl и других средств, которые позволяют указывать только выходной каталог или полное имя файла.

## <a name="parameters"></a>Параметры

В следующей таблице описаны параметры задачи **GetOutputFileName**.

|Параметр|Description|
|---------------|-----------------|
|**OutputExtension**|Обязательный параметр **string**.|
|**OutputFile**|Необязательный параметр вывода типа **string**.|
|**OutputPath**|Необязательный параметр типа **string**.|
|**SourceFile**|Обязательный параметр **string**.|

## <a name="see-also"></a>См. также раздел

[Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
