---
title: Добавление параметров командной строки | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de0044544a97134380900d3e55f54c8fb34431fd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352336"
---
# <a name="add-command-line-switches"></a>Добавить параметры командной строки
Можно добавить параметры командной строки, которые применяются к VSPackage при *devenv.exe* выполняется. Используйте <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> для объявления имени параметра и его свойств. В этом примере добавляется параметр MySwitch для подкласса VSPackage с именем **AddCommandSwitchPackage** без аргументов и с пакетом VSPackage, загружаются автоматически.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 Именованные параметры отображаются в следующих описаниях.

||||
|-|-|-|-|
| Параметр | Описание|
| Аргументы | Число аргументов для параметра. Может быть «*», или список аргументов. |
| DemandLoad | Загрузите пакет VSPackage автоматически, если задано значение 1, в противном случае — значение 0. |
| HelpString | Строка или ресурс идентификатор справки строки для отображения с **devenv /?** . |
| name | Переключатель. |
| PackageGuid | Идентификатор GUID пакета. |

 Первое значение аргументов обычно 0 или 1. Специальное значение "*" может использоваться для указания, что весь остаток командной строки — это аргумент. Это может быть полезно для отладки сценариев, где пользователь должен пройти в командной строке отладчика.

 Имеет значение DemandLoad `true` (1) или `false` (0) указывает, что VSPackage должны загружаться автоматически.

 HelpString значение — идентификатор ресурса строки, который отображается в **devenv /?** Отображение справки. Это значение должно быть в форме «#nnn» где nnn — целое число. Строковое значение в файле ресурсов должна завершиться в символ новой строки.

 Значение имени является имя коммутатора.

 Значение PackageGuid – идентификатор GUID пакета, который реализует этот переключатель. Интегрированная среда разработки использует этот идентификатор GUID для поиска VSPackage в реестре, к которому применяется параметр командной строки.

## <a name="retrieve-command-line-switches"></a>Получить параметры командной строки
 Когда загружается пакет, параметры командной строки можно получить, выполнив следующие действия.

1. В ваш VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализации, вызов `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> для получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> интерфейс.

2. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> для получения параметров командной строки, введенные пользователем.

   Приведенный ниже показано, как узнать ли параметра командной строки MySwitch введенный пользователем:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 Отвечает на наличие параметров командной строки каждый раз, когда загружается пакет.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Параметры командной строки для devenv](../ide/reference/devenv-command-line-switches.md)
- [Служебная программа CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)
- [. Файлов pkgdef](/visualstudio/extensibility/shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file)