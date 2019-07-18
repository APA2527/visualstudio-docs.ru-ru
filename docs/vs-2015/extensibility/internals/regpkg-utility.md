---
title: Служебная программа RegPkg | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1895d3b57e5109f824728021cb1d64f0c527384b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436587"
---
# <a name="regpkg-utility"></a>Служебная программа RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> С помощью файлах pkgdef — предпочтительный способ зарегистрировать пакеты в Visual Studio. Это позволяет расширение развертывания без доступа в системный реестр, который требуется для развертывания VSIX. Файлов pkgdef создаются с помощью [программа CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Дополнительные сведения о развертывании пакета Visual Studio, см. в разделе [доставка расширений Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 Служебную программу RegPkg.exe регистрирует VSPackage с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и подготавливает его для развертывания. Эта служебная программа используется скрытно, во время разработки пакета VSPackage. Он выполняется как часть процесса построения, чтобы вы можно собрать и запустить пакет VSPackage в экспериментальном кусте.  
  
 RegPkg можно создавать скрипты реестра системы в нескольких форматах. Можно включить эти скрипты в проектах развертывания, например в проектах MSI-файл или файлы Windows Installer XML Toolset.  
  
 RegPkg.exe обычно находится в \< *путь установки Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg придерживается следующего синтаксиса:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 Выполняет регистрацию под указанным  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] корневой элемент.  
  
 /regfile:FileName  
 Создает REG-файл, а не обновления реестра.  Не может использоваться с /vrgfile или /rgsfile или /wixfile.  
  
 /rgsfile:FileName  
 Создает RGS-файл, а не обновления реестра.  Не может использоваться с /vrgfile или/regfile или /wixfile.  
  
 /vrgfile:FileName  
 Создает файл .vrg вместо обновления реестра.  Не может использоваться с/regfile или /rgsfile или /wixfile.  
  
 /rgm  
 Создает файл .rgm помимо RGS-файл.  Должны быть объединены с /rgsfile.  
  
 /wixfile:FileName  
 Создает набор инструментов Windows Installer XML-совместимый файл, а не обновления реестра.  Не может использоваться с/regfile или /rgsfile или /vrgfile.  
  
 /codebase  
 Регистрация силы в базе кода, а не сборка.  
  
 / Assembly  
 Регистрация силы в сборку, а не в базе кода.  
  
 / unregister  
 Отменяет регистрацию этого пакета.  Нельзя использовать  
  
 / regfile или /vrgfile или /rgsfile /wixfile.  
  
## <a name="see-also"></a>См. также  
 [Выпуск продукта](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Устранение неполадок регистрации пакета RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
