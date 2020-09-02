---
title: Открытие модели UML с помощью Visual Studio API | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, opening models in Visual Studio
ms.assetid: 38423682-f2a7-4d2a-a2cd-fd680e9b4b4d
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 694f10fb0af440513331aa6e76dbf9a59a16d340
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668506"
---
# <a name="open-a-uml-model-by-using-the-visual-studio-api"></a>Открытие модели UML с помощью API Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Модели и схемы также можно открыть в пользовательском интерфейсе Visual Studio с помощью API.

 Если нужно только прочитать модель в программном коде, не показывая ее пользователю, можно воспользоваться указанными ниже методами.

- Шина модели Visual Studio позволяет получить доступ к моделям и элементам внутри них, а также предоставляет стандартный метод создания связей между моделями. Дополнительные сведения см. [в разделе Интеграция моделей UML с другими моделями и инструментами](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- Модель можно открыть в режиме только для чтения. Дополнительные сведения см. [в разделе Чтение модели UML в программном коде](../modeling/read-a-uml-model-in-program-code.md).

## <a name="opening-models-and-diagrams-in-visual-studio"></a><a name="Showing"></a> Открытие моделей и схем в Visual Studio
 Чтобы открыть модель в пользовательском интерфейсе, воспользуйтесь стандартным API-интерфейсами Visual Studio `EnvDTE.DTE`. Существует два полезных приведения, которые можно применять к элементам проекта моделирования.

- `EnvDTE.Project` можно привести к и из `IModelingProject` , если проект является проектом моделирования и если проект загружен в текущий домен приложения.

- `EnvDTE.ProjectItem` можно привести к и из `IDiagramContext` , если элемент является схемой UML.

  Для приведенного ниже примера в проект необходимо импортировать следующие ссылки:

- EnvDTE

- Microsoft.VisualStudio.ArchitectureTools.Extensibility

- Microsoft.VisualStudio.Modeling.Sdk.[версия]

- Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[версия]

- Microsoft.VisualStudio.Shell.Immutable.[версия]

- Microsoft.VisualStudio.Uml.Interfaces

- System.ComponentModel.Composition

  В этом примере модель UML открывается в Visual Studio.

```
using EnvDTE; // Visual Studio API for loading diagrams
using
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   // for ICommandExtension and other handler types
using Microsoft.VisualStudio.Uml.Classes;
   // for basic UML types
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   // for model construction methods
using EnvDTE;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
                             // for IDiagram
...
```

 В расширении Visual Studio можно сделать следующее объявление, чтобы получить доступ к поставщику служб узла:

```
[Import] public Microsoft.VisualStudio.Shell.SVsServiceProvider ServiceProvider {get;set;}
...
```

 Посредством метода можно получить доступ к проекту, например текущему проекту.

```
DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;
IModelingProject modelingProject = project as IModelingProject;
if (modelingProject == null) return; // not a modeling project

// Access the model's store and contents.
IModelStore store = modelingProject.Store;
foreach (IElement element in store.Root.OwnedElements) {...}

// Open all the project's diagrams.
foreach (ProjectItem item in project.ProjectItems)
{
     IDiagramContext modelingItem = item as IDiagramContext;
     if (modelingItem == null)
         continue; // not a model diagram
     IDiagram diagram = modelingItem.CurrentDiagram;
     if (diagram == null)
     {
        // Diagram is closed. Open it.
        item.Open().Activate();
        diagram = modelingItem.CurrentDiagram;
     }
     // Access the shapes.
     foreach (IShape<IElement> shape
               in diagram.GetChildShapes<IElement>())
     {
       IElement displayedElement = shape.Element;
       ...
     }
   }
}
```

## <a name="see-also"></a>См. также:
 [Программирование с помощью API UML](../modeling/programming-with-the-uml-api.md) [расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)
