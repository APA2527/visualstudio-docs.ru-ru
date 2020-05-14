---
title: "\"Параметры\", \"Текстовый редактор\", JavaScript, \"Анализ кода\""
ms.date: 1/15/2019
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Linting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Linting
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Linting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Linting
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f8a194f3848b0737fc33af2b9948102987a5923
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "68605964"
---
# <a name="options-dialog-box-text-editor--javascripttypescript--linting"></a>Диалоговое окно "Параметры": Текстовый редактор \> JavaScript/TypeScript \> Анализ кода

Страница **Анализ кода** диалогового окна **Параметры** позволяет задавать параметры анализа кода в редакторе кода. Чтобы открыть эту страницу, выберите в строке меню **Сервис** > **Параметры**, затем разверните **Текстовый редактор** > **JavaScript/TypeScript** > **Анализ кода**.

## <a name="eslint-settings"></a>Параметры ESLint

Эти параметры позволяют включить статический анализ кода JavaScript и TypeScript и выбрать файлы для анализа. Дополнительные сведения об ESLint см. на веб-сайте [ESLint.org](https://eslint.org/).

### <a name="uielement-list"></a>Список элементов пользовательского интерфейса

|Параметр|Описание|
|------------|-----------------|
|**Включить ESLint**|Если выбран этот параметр, в редакторе кода можно выполнять статический анализ кода.|
|**Lint all files included in project, even closed files** (Проанализировать все файлы, включенные в проект, даже закрытые)|Если этот параметр выбран, анализируются закрытые файлы, если не предусмотрена диагностика только открытых файлов.|

## <a name="global-eslint-config-options"></a>Global ESLint Config Options (Параметры глобальной конфигурации ESLint)

Этот параметр позволяет скопировать расположение файла глобальной конфигурации ESLint. Кроме того, если ранее вы меняли расположение файла, можно восстановить его расположение по умолчанию.

## <a name="see-also"></a>См. также

- [Страница "Общие", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/general-environment-options-dialog-box.md)