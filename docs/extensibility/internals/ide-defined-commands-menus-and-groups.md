---
title: Команды, определенные в интегрированной среде разработки, меню и групп | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 727c999e275830260ce83eac3d2d72024e89882b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909868"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Команды, меню и группы, определенные в интегрированной среде разработки
Меню, команд и группы команд уже определены для использования [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки. Эти команды также доступны для использования при расширении [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="finding-environment-defined-commands"></a>Поиск команды, определенные в среде
 Команды среды определяются в набор четырех vsct-файлы:

- SharedCmdDef.vsct

- SharedCmdPlace.vsct

- ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Эти файлы расположены в  *\<путь установки пакета SDK для Visual Studio >* \VisualStudioIntegration\Common\Inc\\. Эти файлы содержат определения идентификаторов GUID для меню и групп, которые можно использовать в в файле конфигурации (.vsct) таблицы команд вашего VSPackage как контейнеры для меню, группы и команды.

## <a name="in-this-section"></a>В этом разделе
- [Идентификаторы GUID и идентификаторы меню Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Предоставляет значения GUID и идентификатор меню в строке меню Visual Studio и групп, которые они содержат.

- [Идентификаторы GUID и идентификаторы панелей инструментов Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Предоставляет значения GUID и идентификатор, панелей инструментов в Интегрированной среде разработки Visual Studio и групп, которые они содержат.

- [Идентификаторы GUID и идентификаторы команд Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Предоставляет значения GUID и идентификатор команды, определенные в интегрированной среде разработки Visual Studio.

## <a name="see-also"></a>См. также
- [Файлы таблицы команд Visual Studio (VSCT-файлы)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Команды, определенные в интегрированной среде разработки, для расширения систем проектов](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)