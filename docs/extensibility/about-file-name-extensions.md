---
title: О расширениях имен файлов | Документация Майкрософт
description: Узнайте, как зарегистрировать расширения имен файлов для пакетов VSPackage и связать их с определенной версией Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3f938eb31c06e1e88af21b058b4475bc192d49c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874413"
---
# <a name="about-file-name-extensions"></a>О расширениях имен файлов
При регистрации расширения файла VSPackage его можно связать с версией [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Это важно, если [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] на компьютере установлено более одной версии.

 Расширения файлов для пакетов VSPackage регистрируются в разделе **HKEY_CLASSES_ROOT** Key со значением по умолчанию, которое указывает на связанный программный идентификатор (ProgID).

 В следующем примере показаны сведения о регистрации для расширения файла *VCPROJ* :

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Файлы, связанные с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , должны иметь версию ProgID, например `VisualStudio.vcproj.8.0` . Идентификатор ProgID позволяет параллельно устанавливать продукт для поддержки сопоставлений расширений файлов между версиями продукта. Идентификатор ProgID, зависящий от версии, также позволяет использовать стандартные глаголы, такие как Open, Edit и т. д., без необходимости перезаписи или перезаписи другими приложениями или версиями [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 В некоторых случаях не следует изменять идентификатор ProgID, связанный с расширением файла. Например, ProgID для расширения файла *htm* (ProgID = хтмлфиле) жестко кодируется в ряде мест в операционной системе и широко известен и используется в связи с файлами *htm* и *HTML* .

## <a name="see-also"></a>См. также раздел
- [Регистрация расширений имен файлов для параллельных развертываний](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Определение обработчиков файлов для расширений имен файлов](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
