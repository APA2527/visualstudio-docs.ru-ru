---
title: Регистрация расширений имен файлов для параллельного IDE
description: Сведения о регистрации расширений имен файлов для параллельных развертываний, которые позволяют пользователям открывать файлы в соответствующей версии Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a457a3848917eff3d3722a8e72f0b0b720c0b43b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837007"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Регистрация расширений имен файлов для параллельных развертываний
Для пакетов VSPackage, развернутых в параллельной среде, необходимо зарегистрировать расширения имен файлов, чтобы связать их с правильной версией [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Если вы не используете расширение имени файла для конкретной версии, регистрация позволяет пользователям открыть проект и файлы элементов проекта в соответствующей версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>Содержание раздела
- [О расширениях имен файлов](../extensibility/about-file-name-extensions.md) Описание регистрации расширений имен файлов.

- [Определение обработчиков файлов для расширений имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Содержит сведения о регистрации приложений, которые могут открывать, изменять и т. д., определенного расширения имени файла.

- [Регистрация команд для расширений имен файлов](../extensibility/registering-verbs-for-file-name-extensions.md) Описывает, как зарегистрировать глаголы.

- [Управление параллельными сопоставлениями файлов](../extensibility/managing-side-by-side-file-associations.md) Описывает, как обрабатывать параллельные установки, в которых необходимо вызвать определенную версию, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] чтобы открыть файл.

## <a name="related-sections"></a>Связанные разделы
- [Поддержка нескольких версий Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Описывает проблемы, связанные с несколькими версиями пакета [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage во время разработки и развертывания для конечных пользователей.
