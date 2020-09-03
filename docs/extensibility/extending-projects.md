---
title: Расширение проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14108a304cc5f85c9a870bc66804df7daa98f3ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711749"
---
# <a name="extend-projects"></a>Расширение проектов
Проекты и решения — это способы, с помощью которых Visual Studio организует файлы кода и ресурсов в единицах компиляции и развертывания. Дополнительные сведения о проектах в [проектах (пакет SDK для Visual Studio)](../extensibility/extending-projects.md)см. здесь.

 Вы можете создавать собственные типы проектов с помощью пакета SDK для Visual Studio и платформы управляемого пакета для проектов, которые можно скачать в [среде управляемых пакетов для проектов](https://github.com/tunnelvisionlabs/MPFProj10). Сведения о реализации пользовательских проектов см. в разделе Создание [нового проекта: внутри, части одна](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) и новая возможность [создания проекта: в этой части вторая](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 В подразделах этого раздела описывается создание пользовательских проектов и управление различными типами решений Visual Studio.

## <a name="in-this-section"></a>В этом разделе
- [Создание базовой системы проектов, часть 1](../extensibility/creating-a-basic-project-system-part-1.md) Описывает создание пользовательской системы проектов.

- [Создание базовой системы проектов, часть 2](../extensibility/creating-a-basic-project-system-part-2.md) Описывает создание пользовательской системы проектов.

- [Сохранение данных в файлах проекта](../extensibility/saving-data-in-project-files.md) Объясняет, как добавить в проект (<em>.</em> proj *) файлы.

- [Проверка подтипов проекта во время выполнения](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) Объясняет, как проверить подтип проекта во время выполнения.

- [Добавление и удаление страниц свойств](../extensibility/adding-and-removing-property-pages.md) Объясняет, как настроить страницы свойств для пользовательского проекта.

- [Добавление атрибута в элемент проекта](../extensibility/adding-an-attribute-to-a-project-item.md) Объясняет, как добавить атрибут в пользовательский элемент проекта.

- [Сохранение свойства элемента проекта](../extensibility/persisting-the-property-of-a-project-item.md) Объясняет, как сохранить свойства пользовательского элемента проекта.

- [Управление универсальными проектами Windows](../extensibility/managing-universal-windows-projects.md) Объясняется, как управлять универсальными проектами.
