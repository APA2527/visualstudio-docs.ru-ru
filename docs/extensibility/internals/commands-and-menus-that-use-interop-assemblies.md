---
title: Команды и меню, использующие сборки взаимодействия | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c381abe9b4c6ea2a58342e185d7427fa56a180
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709489"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Команды и меню, использующие сборки взаимодействия
Пакет VSPackage, который реализует команды меню и панели инструментов с помощью сборок взаимодействия, должен:

- Сообщите [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки (IDE) о поддерживаемых командах и о том, включены ли они в данный момент.

- Придерживайтесь правил (контракта) для обработки команд.

- Явная реализация обработки команд с помощью <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейса или.

  В следующем разделе описывается выполнение этих задач.

## <a name="in-this-section"></a>В этом разделе
- [Определение состояния команды с помощью сборок взаимодействия](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Описывает, как VSPackage уведомляет интегрированную среду разработки о том, какие команды она поддерживает, и включены ли они в данный момент.

- [Контракты команд в сборках взаимодействия](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Предоставляет определение базового контракта команды, используемого всеми пакетами VSPackage, которые реализуют команды с помощью сборок взаимодействия.

- [Реализация команды](../../extensibility/internals/command-implementation.md)

 Содержит общие сведения о том, как VSPackage реализует команду.

- [Регистрация обработчиков команд сборки взаимодействия](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Описание записей реестра, необходимых для уведомления интегрированной среды разработки о том, что пакет VSPackage предоставляет обработчик команд.

## <a name="related-sections"></a>Связанные разделы
- [Доступность команды](../../extensibility/internals/command-availability.md)

 Описывает критерии, которые используются интегрированной средой разработки для определения доступности команд VSPackage и объектов, которые их обрабатывает.

- [Как пакеты VSPackage добавляют элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Содержит сведения о создании пользовательского интерфейса, использующего [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поддержку команды.

- [Маршрутизация команд в пакетах VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)

 Обзор процесса, используемого для связи объекта с правильным запросом команды.
