---
title: Задача SetEnv | Документация Майкрософт
ms.date: 11/05/2018
ms.topic: reference
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- SetEnv task (MSBuild (C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59523e3f6b12eb5921235efcf15d7937a14e7247
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595102"
---
# <a name="setenv-task"></a>Задача SetEnv
Задает или удаляет значение указанной переменной среды.

## <a name="parameters"></a>Параметры
 В представленной ниже таблице приводятся параметры задачи **SetEnv**.

|Параметр|Описание|
|---------------|-----------------|
|**Name**|Обязательный параметр **string**.<br /><br /> Имя переменной среды.|
|**OutputEnvironmentVariable**|Необязательный параметр вывода **String**.<br /><br /> Содержит значение, которое присвоено переменной среды, заданной в параметре **Name**.|
|**Prefix**|Обязательный параметр `Boolean`.<br /><br /> Если он имеет значение `true`, значение параметра **Value** сцепляется со значением переменной среды, указанной в параметре **Name**, и результат присваивается этой переменной среды. Если `false`, переменной среды присваивается только значение **Value**.|
|**Целевой объект**|Необязательный параметр типа **String**.<br /><br /> Задает расположение, в котором хранится переменная среды. Укажите "Пользователь" или "Компьютер".<br /><br /> Дополнительные сведения см. в статье [Перечисление EnvironmentVariableTarget](xref:System.EnvironmentVariableTarget).|
|**Значение**|Необязательный параметр типа **String**.<br /><br /> Значение, которое присваивается переменной среды, заданной в параметре **Name**. Если поле **Value** пусто, но переменная существует, то она удаляется. Если переменная не существует, ошибка не происходит, даже несмотря на невозможность выполнения операции.<br /><br /> Дополнительные сведения см. в статье [Метод Environment::SetEnvironmentVariable](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>См. также
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
