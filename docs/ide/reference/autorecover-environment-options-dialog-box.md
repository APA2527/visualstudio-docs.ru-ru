---
title: Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры"
description: Сведения о диалоговом окне "Параметры" в разделе "Среда" на странице "Автовосстановление" и о том, как использовать его для настройки автоматического резервного копирования файлов.
ms.custom: SEO-VS-2020
ms.date: 08/14/2020
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b578e914c6fa099528008090646372c7d9ef26b1
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871357"
---
# <a name="autorecover-environment-options-dialog-box"></a>Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры"

Эта страница диалогового окна **Параметры** служит для настройки автоматического резервного копирования файлов. Можно указать необходимость восстановления измененных файлов в случае неожиданного завершения работы Visual Studio.

Чтобы открыть это диалоговое окно, последовательно выберите в меню пункты **Инструменты** > **Параметры** > **Среда** > **Автовосстановление**.

:::image type="content" source="media/autorecover-options.png" alt-text="Снимок экрана: раздел &quot;Автовосстановление&quot; в диалоговом окне &quot;Параметры&quot;":::

**Сохранять данные автовосстановления каждые [n] мин**

::: moniker range="vs-2019"

Используйте этот параметр, чтобы настроить периодичность автоматического сохранения файла в редакторе. Что касается ранее сохраненных файлов, Visual Studio 2019 версии 16.2 и более поздних версий сохраняет копию файла в папке **_%LocalAppData%\Microsoft\VisualStudio\BackupFiles\\[имя_проекта]_* _. Если этот файл новый и еще не был сохранен, Visual Studio автоматически сохраняет его, используя случайно созданное имя файла.

> [!NOTE]
> Если вы используете Visual Studio 2019 версии 16.1 или более ранней версии, файл будет расположен в папке _%USERPROFILE%\Documents\Visual Studio [версия]\Backup Files\\[имя_проекта]*. Дополнительные сведения см. в [журнале заметок о выпуске Visual Studio 2019](/visualstudio/releases/2019/release-notes-history/).

::: moniker-end

::: moniker range="vs-2017"

Используйте этот параметр, чтобы настроить периодичность автоматического сохранения файла в редакторе. Для ранее сохраненных файлов Visual Studio 2017 сохраняет копию файла в папке *%USERPROFILE%\Documents\Visual Studio [версия]\Backup Files\\[имя проекта]* . Если этот файл новый и еще не был сохранен, Visual Studio автоматически сохраняет его, используя случайно созданное имя файла.

::: moniker-end

**Хранить данные автовосстановления [n] дн.**

Используйте этот параметр, чтобы указать период, в течение которого Visual Studio будет хранить файлы, созданные для автоматического восстановления.

### <a name="see-also"></a>См. также раздел

- [Параметры - диалоговое окно](../../ide/reference/options-dialog-box-visual-studio.md)
