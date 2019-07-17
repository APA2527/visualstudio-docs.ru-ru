---
title: Средство Windows в реестре | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cedb95ccd98c3d5bd5e05086cfd1b53b0f97cd9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186388"
---
# <a name="tool-windows-in-the-registry"></a>Окно инструментов в реестре
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Необходимо зарегистрировать пакетов VSPackage, предоставляющих окон инструментов [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] как средство поставщиков окна. Окна инструментов, созданные с помощью шаблона пакета Visual Studio для этого по умолчанию. Поставщиков окна инструментов, используют разделы реестра системы, которые указывают атрибуты видимости, такие как размер окна инструментов по умолчанию и расположение, идентификатор GUID окна, который служит в качестве область окна инструментов, а также стиль закрепления.  
  
 Во время разработки поставщики управляемых инструментов окна зарегистрировать окон инструментов, добавление атрибутов к исходному коду, а затем выполнив служебную программу RegPkg.exe в результирующей сборке. Дополнительные сведения см. в разделе [регистрация окна инструментов](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Регистрация поставщиков окна неуправляемых средство  
 Поставщики неуправляемых средство окна необходимо зарегистрировать в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] в разделе ToolWindows в системный реестр. Следующие фрагменте REG-файла показано, как могут быть зарегистрированы динамического окна инструментов.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 В первый ключ в приведенном выше примере, номер версии — версия [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], такие как 7.1 или 8.0, подраздел {f0e1e9a1-9860-484d-ad5d-367d79aabf55} — это идентификатор GUID панели окна инструментов (DynamicWindowPane), а также {значение по умолчанию 01069cdd-95ce-4620-ac21-ddff6c57f012} является GUID VSPackage, предоставляющий окна инструментов. Описание типа Float и DontForceCreate подразделов, см. в разделе [конфигурацию отображаемое окно средства](../extensibility/tool-window-display-configuration.md).  
  
 Второй необязательный ключ ToolWindows\Visibility, указывает идентификаторы GUID команды, требующие окна инструментов, чтобы стать видимыми. В этом случае существует команды не указан. Дополнительные сведения см. в разделе [конфигурацию отображаемое окно средства](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Основные сведения о пакетах VSPackage](../misc/vspackage-essentials.md)
