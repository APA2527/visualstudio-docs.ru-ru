---
title: Чтение модели UML в программном коде | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, reading models
ms.assetid: 0f63105e-6079-498a-94f1-318c0f5f9621
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 37539ee6c031d88b9db279cc61214ac5e3077e76
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387666"
---
# <a name="read-a-uml-model-in-program-code"></a>Чтение модели UML в программном коде
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете загрузить модель UML и ее схемы, используя UML API.  
  
## <a name="Reading"></a> Чтение модели в программном коде  
 Чтобы получить доступ к содержимому модели, не отображая ее в окне [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], используйте метод `ModelingProject.LoadReadOnly()`.  
  
 Пример:  
  
```  
using Microsoft.VisualStudio.Uml.Classes;   
               // for IElement  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;   
               // for ModelingProject  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
               // for IModelStore  
...   
string projectPath = @"C:\MyProjectFolder\MyProject.modelproj";  
using (IModelingProjectReader projectReader =  
           ModelingProject.LoadReadOnly(projectPath))  
{  
   IModelStore store = projectReader.Store;  
   foreach (IClass umlClass in store.AllInstances<IClass>())  
   {   
       ...  
   }  
}  
```  
  
 Если нужно прочитать фигуры на схеме, необходимо сначала прочитать проект, а затем схему.  
  
 Пример:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
                             // for IDiagram  
...  
foreach (string diagramFile in projectReader. DiagramFileNames)  
{   
  IDiagram diagram = projectReader.LoadDiagram(diagramFile);  
  foreach (IShape<IElement> shape   
         in diagram.GetChildShapes<IElement>())  
  { ... }  
}  
```  
  
## <a name="alternative-methods"></a>Альтернативные методы  
 Для многих приложений [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Modelbus позволяет ссылаться на модели и элементы внутри них, обеспечивая большую надежность и гибкость, чем с помощью методов, описанных в этом разделе. Она предоставляет стандартный метод создания ссылок между произвольными элементами в одной модели или разных моделях. Дополнительные сведения см. в разделе [интеграция моделей UML с другими моделями и средствами](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
 Кроме того, с помощью API-интерфейса [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] можно открывать модели и схемы в пользовательском интерфейсе. Дополнительные сведения см. в разделе [Открытие модели UML с помощью Visual Studio API](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).  
  
## <a name="Standalone"></a> Автономные приложения  
 Пример из предыдущего подраздела можно выполнить в расширениях Visual Studio. Можно прочитать модель в отдельном приложении, однако необходимо добавить несколько ссылок на проект [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
> [!NOTE]
> Вероятно, способы прочтения модели в отдельном приложении будут изменены в последующих выпусках продукта. Некоторые функции, доступные в текущей версии, могут оказаться недоступными в последующих выпусках.  
  
#### <a name="to-add-references-to-read-a-model-in-a-stand-alone-application"></a>Добавление ссылок для чтения модели в отдельном приложении  
  
1. В обозревателе решений щелкните правой кнопкой мыши проект, в котором выполняется сборка приложения и нажмите кнопку **свойства**. В редакторе свойств в **приложения** вкладке **требуемой версии .NET Framework** до требуемой версии платформы .NET Framework.  
  
2. Добавьте ссылки [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)], необходимые для доступа к моделям UML, например:  
  
   - Microsoft.VisualStudio.Uml.Interfaces.dll  
  
   - Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll  
  
3. Помимо ссылок, перечисленных в предыдущих разделах, добавьте в проект следующие ссылки из **\Common7\IDE\PrivateAssemblies Visual Studio [версия] \Program Files\Microsoft**:  
  
   - Microsoft.VisualStudio.Uml.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.ModelStore.Dsl.dll  
  
     Если нужно обеспечить возможность чтения схем в приложении, потребуются также следующие ссылки:  
  
   - Microsoft.VisualStudio.TeamArchitect.ActivityDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.ComponentDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.LogicalClassDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.SequenceDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.UseCase.Dsl.dll  
  
## <a name="see-also"></a>См. также  
 [Программирование с UML API](../modeling/programming-with-the-uml-api.md)   
 [Расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)
