---
title: Служебная программа RegPkg | Документация Майкрософт
description: Узнайте, как служебная программа RegPkg.exe регистрирует пакет VSPackage в Visual Studio и готовит его к развертыванию.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2f0ddf9c707de0b30b18761ba5af1ef42e198231
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837251"
---
# <a name="regpkg-utility"></a>Служебная программа RegPkg
> [!NOTE]
> Для регистрации пакетов в Visual Studio предпочтительным способом является использование файлов pkgdef. Это позволяет развертывать расширения без доступа к системному реестру, что является требованием для развертывания VSIX. Файлы pkgdef создаются с помощью [служебной программы CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Дополнительные сведения о развертывании пакетов Visual Studio см. в разделе [Доставка расширений Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

 Служебная программа RegPkg.exe регистрирует пакет VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и готовит его к развертыванию. Эта служебная программа используется в фоновом режиме во время разработки VSPackage. Он выполняется как часть процесса сборки, чтобы вы могли создать и запустить VSPackage в экспериментальном Hive.

 RegPkg может создавать сценарии системного реестра в нескольких форматах. Эти скрипты можно включить в проекты развертывания, такие как MSI-проекты или установщик Windows файлы набора инструментов XML.

 RegPkg.exe обычно находится в \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg соответствует этому синтаксису:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root: root выполняет регистрацию в указанном

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] корневой.

 /regfile: FileName создает reg-файл, а не обновляет реестр.  Не может использоваться с/вргфиле или/ргсфиле или/виксфиле.

 /ргсфиле: FileName создает RGS-файл, а не обновляет реестр.  Не может использоваться с/вргфиле или/regfile или/виксфиле.

 /вргфиле: FileName создает ВРГ-файл, а не обновляет реестр.  Нельзя использовать с/regfile или/ргсфиле или/виксфиле.

 /РГМ создает РГМ-файл в дополнение к RGS-файлу.  Необходимо сочетать с/ргсфиле.

 /виксфиле: FileName создает файл, совместимый с набором инструментов установщик Windows XML, вместо обновления реестра.  Нельзя использовать с/regfile или/ргсфиле или/вргфиле.

 /CodeBase принудительно выполняет регистрацию с использованием базы кода, а не сборки.

 /Assembly принудительно выполняет регистрацию с помощью сборки, а не базы кода.

 /Unregister отменяет регистрацию этого пакета.  Не может использоваться

 с/regfile или/вргфиле или/ргсфиле или/виксфиле.

## <a name="see-also"></a>См. также раздел
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Устранение неполадок регистрации пакета RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
