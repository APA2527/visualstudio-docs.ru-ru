---
title: Командная таблица Visual Studio (. Vsct) файлы | Документация Майкрософт
description: Сведения о файлах конфигурации таблицы команд, которые представляют собой текстовые файлы, описывающие набор команд, содержащихся в VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 377bae52f506c1cb9ac0f6b2d4136faaab0b50ad
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488041"
---
# <a name="visual-studio-command-table-vsct-files"></a>Файлы таблицы команд Visual Studio (VSCT-файлы)
Файл конфигурации командной таблицы — это текстовый файл, описывающий набор команд, содержащихся в VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Компилятор командной таблицы (VSCT) компилирует файлы конфигурации на основе XML (VSCT-файлы) в двоичные файлы командных таблиц (. CTO). Результирующие CTO-файлы те же, что создаются с помощью компилятора командной таблицы (CTC) для компиляции файлов конфигурации CTC. Однако vsct-файлы на основе XML имеют некоторые преимущества, такие как редактор XML и IntelliSense XML.

 Дополнительные сведения о синтаксисе и семантике vsct-файлов см. в разделе [Разработка командной таблицы XML (. Vsct) файлы](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>В этом разделе
 [Разработка файлов таблицы команд XML (VSCT-файлы)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 Описывает, как проектировать файлы vsct.

 [Практическое руководство. Создание VSCT-файла](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Сравнивает методы создания vsct-файла. Описывает процесс создания нового vsct-файла вручную.

## <a name="related-sections"></a>Связанные разделы
 [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md)

 Предоставляет сведения о каждом разделе XML-файла конфигурации в таблице команд.

 [Конфигурация таблицы команд (. CTC)](/previous-versions/bb165153(v=vs.100)) содержит общие сведения о нерекомендуемом формате файла CTC.

 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Описывает спецификацию формата командной таблицы.

 [Ресурсы в пакетах VSPackage](../../extensibility/internals/resources-in-vspackages.md)

 Описывает, как использовать управляемые и неуправляемые ресурсы в управляемых пакетах VSPackage.

 [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)

 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.