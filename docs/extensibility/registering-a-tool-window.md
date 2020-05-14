---
title: Регистрация окна инструмента (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e7971de5ae5301d99147bbfc374dda6b039662a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701602"
---
# <a name="register-a-tool-window"></a>Регистрация окна инструмента
Вы можете зарегистрировать окна <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>инструмента, используя и .

## <a name="example"></a>Пример

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 В приведенном выше <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> коде `PersistedWindowPane` `DynamicWindowPane` регистрируется окна инструментов с Visual Studio. Упорный окне инструмента пристыкован и вкладка с **Solution Explorer**, и динамическое окно дается исходное положение по умолчанию и размер. Динамическое окно сделано переходным, что указывает на то, что оно не создается при запуске. Это записывает `DontForceCreate` значение `ToolWindows` в ключе в реестре системы. Для получения дополнительной [Tool window display configuration](/visualstudio/extensibility/tool-window-display-configuration?view=vs-2015)информации см.
