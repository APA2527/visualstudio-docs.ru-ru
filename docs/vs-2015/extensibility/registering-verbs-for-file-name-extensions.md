---
title: Регистрация команд для расширений имен файлов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dbd97310163a4eb3ae5502c6341dc73322ca653d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685272"
---
# <a name="registering-verbs-for-file-name-extensions"></a>Регистрация команд для расширений имен файлов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Сопоставление расширения имени файла с приложением, как правило, имеет предпочитаемым действием, которое происходит при двойном щелчке файла. Этот предпочитаемый действия связанного действия, например открытым, соответствующее действие.  
  
 Вы можете зарегистрировать команд, которые связаны с программный идентификатор (ProgID) для расширения с помощью оболочки раздел, расположенный в HKEY_CLASSES_ROOT\\*progid*\shell. Дополнительные сведения см. в разделе [типы файлов](https://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## <a name="registering-standard-verbs"></a>Регистрация стандартных команд  
 Операционная система распознает следующие стандартные команды:  
  
- Открыть  
  
- Правка  
  
- Воспроизвести  
  
- Print  
  
- Предварительный просмотр  
  
  Когда это возможно, зарегистрируйте обычного глагола. Наиболее распространенным вариантом является командой Open. Используйте команды редактирования только в том случае, если есть различие между при открытии файла и редактирования файла. Например открытие htm-файл отображается в браузере, тогда как редактирование htm-файл запускает редактор HTML. Стандартные команды локализуются с языковым стандартом операционной системы.  
  
> [!NOTE]
> При регистрации стандартных команд, не устанавливайте значение по умолчанию для открытых ключей. Значение по умолчанию содержит строку отображаемого в меню. Операционная система предоставляет этой строки для стандартных команд.  
  
 Файлы проекта должен быть зарегистрирован запустить новый экземпляр класса [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] при открытии файла. В следующем примере показан стандартный глагол регистрацию для [!INCLUDE[csprcs](../includes/csprcs-md.md)] проекта.  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 Чтобы открыть файл в существующий экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], зарегистрируйте ключ DDEEXEC. В следующем примере показан стандартный глагол регистрацию для [!INCLUDE[csprcs](../includes/csprcs-md.md)] CS-файл.  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## <a name="setting-the-default-verb"></a>Настройка действия по умолчанию  
 Действия по умолчанию — это действие, которое выполняется, когда пользователь дважды щелкает в окне проводника Windows. Действия по умолчанию — это команда, указанный в качестве значения по умолчанию для HKEY_CLASSES_ROOT\\*progid*\Shell ключ. Если значение не указано, команда по умолчанию является первой команды, указанной в разделе HKEY_CLASSES_ROOT\\*progid*\Shell список ключей.  
  
> [!NOTE]
> Если вы планируете изменить команду по умолчанию для расширения в развертывании side-by-side, учитывайте влияние на установке и удалению. Во время установки будет перезаписана исходного значения по умолчанию.  
  
## <a name="see-also"></a>См. также  
 [Управление параллельными сопоставлениями файлов](../extensibility/managing-side-by-side-file-associations.md)
