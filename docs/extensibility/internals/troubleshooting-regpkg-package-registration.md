---
title: Устранение неполадок регистрации пакета RegPkg | Документация Майкрософт
description: Используйте эти сведения для устранения неполадок с регистрацией пакетов RegPkg в Visual Studio. Используйте версию RegPkg, подходящую для вашего пакета.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eef67b86925bc38a317196bbf00860b75a6ee15c
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487716"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Устранение неполадок регистрации пакета RegPkg
> [!NOTE]
> Для регистрации пакетов в Visual Studio предпочтительным способом является использование файлов pkgdef. Это позволяет развертывать расширения без доступа к системному реестру. Файлы pkgdef создаются с помощью [служебной программы CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Чтобы зарегистрировать пакет с помощью RegPkg в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , необходимо использовать версию regpkg, подходящую для вашего пакета.

## <a name="regpkg-versions-related-to-package-versions"></a>Версии RegPkg, связанные с версиями пакетов
 Существует две версии RegPkg. Одна версия включена в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Используйте эту версию для регистрации пакетов, созданных с помощью одной из следующих сборок:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Он не может зарегистрировать пакеты, созданные с помощью предыдущей Microsoft.VisualStudio.Shell.dll сборки.

   Более ранняя версия RegPkg может регистрировать пакеты, созданные с помощью сборки Microsoft.VisualStudio.Shell.dll. Однако он не может зарегистрировать пакеты, созданные с помощью более поздних версий этой сборки.

## <a name="see-also"></a>См. также раздел
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Устранение неполадок в Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
