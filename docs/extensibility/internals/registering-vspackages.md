---
title: Регистрация пакетов VSPackage | Документация Майкрософт
description: Файл pkgdef содержит сведения, которые в противном случае были бы добавлены в системный реестр. Узнайте, как в Visual Studio используются файлы pkgdef для описания или размещения VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae4d7ae70766b7e0d2d8eedb5d79d97159839146
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875119"
---
# <a name="registering-vspackages"></a>Регистрация пакетов VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует файлы pkgdef для описания и размещения VSPackage. Файл pkgdef содержит все сведения о регистрации, которые в противном случае были бы добавлены в системный реестр. Управляемые пакеты VSPackage регистрируются путем добавления атрибутов в исходный код, а затем запуска [служебной программы CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) в результирующей сборке для создания файла pkgdef.

## <a name="in-this-section"></a>В этом разделе
- [Выбор расположения файла VSPackage к оболочке Visual Studio](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Описывает путь загрузки пакетов VSPackage.

- [Регистрация и отмена регистрации пакетов VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)

 Описание процесса регистрации VSPackage.
