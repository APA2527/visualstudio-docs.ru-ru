---
title: Задача FormatVersion | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b36c4eb63c503132aaf434c64249e4a5fdd3872
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595258"
---
# <a name="formatversion-task"></a>Задача FormatVersion
Добавляет номер редакции к номеру версии.

- Случай 1. Вход: Version=\<не определена>; Revision=\<неважно>; выходные данные: OutputVersion="1.0.0.0"

- Случай 2. Вход: Version="1.0.0.*"  Revision="5"; выходные данные: OutputVersion="1.0.0.5"

- Случай 3. Вход: Version="1.0.0.0"  Revision=\<неважно>; выходные данные: OutputVersion="1.0.0.0"

## <a name="parameters"></a>Параметры
 В следующей таблице приводятся параметры задачи `FormatVersion` .

|Параметр|Описание|
|---------------|-----------------|
|`FormatType`|Необязательный параметр `String`.<br /><br /> Определяет тип формата.<br /><br /> — "Version" = версия.<br />— "Path" = замените "." на "_".|
|`OutputVersion`|Необязательный выходной параметр `String`.<br /><br /> Указывает выходную версию, содержащую номер редакции.|
|`Revision`|Необязательный параметр `Int32`.<br /><br /> Указывает редакцию, добавляемую к версии.|
|`Version`|Необязательный параметр `String`.<br /><br /> Указывает строку номера версии для форматирования.|

## <a name="remarks"></a>Примечания
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
