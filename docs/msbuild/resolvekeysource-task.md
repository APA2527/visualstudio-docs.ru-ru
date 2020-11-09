---
title: Задача ResolveKeySource | Документы Майкрософт
description: Сведения о параметрах задачи ResolveKeySource MSBuild, которая определяет источник ключа строгого имени.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ed7bf0e831153d1120789d97b2a27aa77822a6b
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048586"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource - задача

Определяет источник ключа строгого имени.

## <a name="task-parameters"></a>Параметры задачи

 В следующей таблице приводятся параметры задачи `ResolveKeySource` .

|Параметр|Описание|
|---------------|-----------------|
|`AutoClosePasswordPromptShow`|Необязательный параметр `Int32`.<br /><br /> Возвращает или задает длительность (в секундах) отображения сообщения с обратным отсчетом.|
|`AutoClosePasswordPromptTimeout`|Необязательный параметр `Int32`.<br /><br /> Получает или задает интервал времени в секундах перед закрытием диалогового окна запроса пароля.|
|`CertificateFile`|Необязательный параметр `String`.<br /><br /> Возвращает или задает путь к файлу сертификата.|
|`CertificateThumbprint`|Необязательный параметр `String`.<br /><br /> Возвращает или задает отпечаток сертификата.|
|`KeyFile`|Необязательный параметр `String`.<br /><br /> Возвращает или задает путь к файлу ключа.|
|`ResolvedKeyContainer`|Необязательный выходной параметр `String`.<br /><br /> Получает или задает разрешенный контейнер ключа.|
|`ResolvedKeyFile`|Необязательный выходной параметр `String`.<br /><br /> Получает или задает разрешенный файл ключа.|
|`ResolvedThumbprint`|Необязательный выходной параметр `String`.<br /><br /> Возвращает или задает отпечаток разрешенного сертификата.|
|`ShowImportDialogDespitePreviousFailures`|Необязательный параметр `Boolean`.<br /><br /> Если задано значение `true`, нужно отображать диалоговое окно импорта, несмотря на предыдущие сбои.|
|`SuppressAutoClosePasswordPrompt`|Необязательный параметр `Boolean`.<br /><br /> Получает или задает логическое значение, указывающее, закрывается ли диалоговое окно запроса пароля автоматически.|

## <a name="remarks"></a>Примечания

 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также раздел

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
