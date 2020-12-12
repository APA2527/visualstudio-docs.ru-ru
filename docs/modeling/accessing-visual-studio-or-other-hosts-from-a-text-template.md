---
title: Обращение к Visual Studio или другим основным приложениям из текстового шаблона
description: Узнайте, как можно использовать методы и свойства в текстовом шаблоне, предоставляемом узлом, который выполняет шаблон.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4c0f19f96ee5f6879ccc3328c29d0e1fa1d2a6d0
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362253"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Доступ к Visual Studio или другим узлам из текстового шаблона

В текстовом шаблоне можно использовать методы и свойства, предоставляемые узлом, который выполняет шаблон. Visual Studio — это пример узла.

> [!NOTE]
> Методы и свойства ведущего приложения можно использовать в обычных текстовых шаблонах, но не в *предварительно обработанных* текстовых шаблонах.

## <a name="obtain-access-to-the-host"></a>Получение доступа к узлу

Чтобы получить доступ к узлу, задайте `hostspecific="true"` в `template` директиве. Теперь можно использовать `this.Host` , который имеет тип [итексттемплатинженгинехост](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Тип [итексттемплатинженгинехост](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) содержит члены, которые можно использовать для разрешения имен файлов и регистрации ошибок, например.

### <a name="resolve-file-names"></a>Разрешение имен файлов

Чтобы найти полный путь к файлу относительно текстового шаблона, используйте `this.Host.ResolvePath()` .

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

### <a name="display-error-messages"></a>Отображение сообщений об ошибках

В этом примере сообщения записываются при преобразовании шаблона. Если узел является Visual Studio, ошибки добавляются в **Список ошибок**.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>
```

## <a name="use-the-visual-studio-api"></a>Использование API Visual Studio

Если вы выполняете текстовый шаблон в Visual Studio, вы можете использовать `this.Host` для доступа к службам, предоставляемым Visual Studio, и любым загруженным пакетам или расширениям.

Задайте hostspecific = "true" и приведите `this.Host` к типу <xref:System.IServiceProvider> .

В этом примере в качестве службы получается API-интерфейс Visual Studio <xref:EnvDTE.DTE> :

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>
```

## <a name="use-hostspecific-with-template-inheritance"></a>Использование hostSpecific с наследованием шаблонов

Укажите `hostspecific="trueFromBase"` , используется ли также `inherits` атрибут, и, если вы наследуете от шаблона, который указывает `hostspecific="true"` . В противном случае может появиться предупреждение компилятора о том, что свойство `Host` объявлено дважды.
