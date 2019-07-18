---
title: Практическое руководство. Расширение конструктора доменного языка | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa807f1b-2780-491e-925b-abbfd31b2bfa
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8c02dbf550ca1621a17d2b674a522e1e4f4bcc1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546945"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>Практическое руководство. Расширение конструктора предметно-ориентированных языков
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Расширения можно создать в конструктор, который позволяет изменять определения DSL. Типы расширения, можно выполнить следующие Добавление команд меню, добавление обработчиков для перетащите и дважды щелкните жестов и правила, которые активируются при изменении определенных типов значений или связей. Расширения можно упаковать как Visual Studio Integration Extension (VSIX) и распределенных другим пользователям.  
  
 Пример кода и Дополнительные сведения об этой функции см. в разделе Visual Studio [визуализации и пакет SDK для моделирования (VMSDK) веб-сайт](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
## <a name="setting-up-the-solution"></a>Настройка решения  
 Настройте проект, содержащий код вашего расширения и проект VSIX, который экспортирует проект. Решение может содержать другие проекты, которые встроены в то же расширение VSIX.  
  
#### <a name="to-create-a-dsl-designer-extension-solution"></a>Для создания решения расширение конструктора доменного языка  
  
1. Создайте новый проект, используя шаблон проекта библиотеки классов. В **новый проект** диалоговом окне щелкните **Visual C#** и затем в среднем окне щелкните **библиотеки классов**.  
  
     Этот проект будет содержать код вашего расширения.  
  
2. Создайте новый проект с помощью шаблона проекта VSIX. В **новый проект** диалогового окна разверните узел **Visual C#**, нажмите кнопку **расширяемости**и затем в среднем окне выберите **проект VSIX**.  
  
     Выберите **добавить решение**.  
  
     Source.Extension.vsixmanifest откроется в редакторе манифестов VSIX.  
  
3. Над полем содержимого щелкните **добавить содержимое**.  
  
4. В **добавить содержимое** диалоговом окне set **выберите тип содержимого** для **компонент MEF**и задайте **проекта** в ваш проект библиотеки классов.  
  
5. Нажмите кнопку **выбрать выпуски** и убедитесь, что **Visual Studio Enterprise** проверяется.  
  
6. Убедитесь, что проект VSIX запускаемым проектом решения.  
  
7. В проекте библиотеки классов добавьте ссылки на следующие сборки:  
  
     Microsoft.VisualStudio.CoreUtility  
  
     Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0;  
  
     System.ComponentModel.Composition  
  
     System.Drawing;  
  
     System.Drawing.Design  
  
     System.Windows.Forms.  
  
## <a name="testing-and-deployment"></a>Тестирование и развертывание  
 Чтобы протестировать любой из расширения в этом разделе, постройте и запустите решение. Откроется экспериментальный экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . В этом случае откройте решение DSL. Измените схему DslDefinition. Можно увидеть расширение поведения.  
  
 Для развертывания расширения к главному [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]и к другим компьютерам, выполните следующие действия:  
  
1. Найдите VSIX-файл установки, в проект VSIX в bin\\*\*\\\*.vsix  
  
2. Скопируйте этот файл на конечном компьютере и проводника Windows (или проводника), дважды щелкните его.  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Откроется диспетчер расширений, убедитесь, что расширение установлено.  
  
   Чтобы удалить расширение, выполните следующие действия.  
  
3. в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]на **средства** меню, щелкните **Диспетчер расширений**.  
  
4. Выберите расширение и удалите его.  
  
## <a name="adding-a-shortcut-menu-command"></a>Добавление команды контекстного меню  
 Чтобы команда меню быстрого доступа к отображаются на поверхности конструктора DSL или в окне обозревателя DSL, напишите класс, аналогичного следующему.  
  
 Класс должен реализовывать `ICommandExtension` и должен иметь атрибут `DslDefinitionModelCommandExtension`.  
  
```  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDesigner;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Command extending the DslDesigner.  
  /// </summary>  
  [DslDefinitionModelCommandExtension]   
  public class MyDslDesignerCommand : ICommandExtension  
  {  
    /// <summary>  
    /// Selection Context for this command  
    /// </summary>  
    [Import]  
    IVsSelectionContext SelectionContext { get; set; }  
  
    /// <summary>  
    /// Is the command visible and active?  
    /// This is called when the user right-clicks.  
    /// </summary>  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Visible = true;  
      // Is there any selected DomainClasses in the Dsl explorer?  
      command.Enabled =   
        SelectionContext.AtLeastOneSelected<DomainClass>();  
  
      // Is there any selected ClassShape on the design surface?  
      command.Enabled |=   
        (SelectionContext.GetCurrentSelection<ClassShape>()  
                .Count() > 0);  
    }  
    /// <summary>  
    /// Executes the command   
    /// </summary>  
    /// <param name="command">Command initiating this action</param>  
    public void Execute(IMenuCommand command)  
    {  
      ...  
    }  
    /// <summary>  
    /// Label for the command  
    /// </summary>  
    public string Text  
    {  
      get { return "My Command"; }  
    }  
  }  
}  
```  
  
## <a name="handling-mouse-gestures"></a>Обработка с помощью жестов мыши  
 Код аналогичен коду команды меню.  
  
```  
[DslDefinitionModelGestureExtension]  
 class MouseGesturesExtensions : IGestureExtension  
 {  
  /// <summary>  
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box  
  /// </summary>  
  /// <param name="targetElement">Shape element on which the user has clicked</param>  
  /// <param name="diagramPointEventArgs">event args for this double-click</param>  
  public void OnDoubleClick(ShapeElement targetElement,  
       DiagramPointEventArgs diagramPointEventArgs)  
  {  
   ModelElement modelElement = PresentationElementHelper.  
        GetDslDefinitionModelElement(targetElement);  
   if (modelElement != null)  
   {  
    MessageBox.Show(string.Format(  
      "Double clicked on {0}", modelElement.ToString()),   
      "Model element double-clicked");  
   }  
  }  
  
  /// <summary>  
  /// Tells if the DslDesigner can consume the to-be-dropped information  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we try to drop</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>  
  public bool CanDragDrop(ShapeElement targetMergeElement,  
        DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    diagramDragEventArgs.Effect = DragDropEffects.Copy;  
    return true;  
   }  
   return false;  
  }  
  
  /// <summary>  
  /// Processes the drop by displaying the dropped text  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we dropped</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    string[] droppedFiles =   
      diagramDragEventArgs.Data.  
               GetData(DataFormats.FileDrop) as string[];  
    MessageBox.Show(string.Format("Dropped text {0}",  
        string.Join("\r\n", droppedFiles)), "Dropped Text");  
   }  
  }  
 }  
```  
  
## <a name="responding-to-value-changes"></a>Реагирование на изменении значения  
 Этот обработчик должен модели домена для правильной работы. Мы предоставляем модель простого предметной области.  
  
```  
using System.Diagnostics;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Rule firing when the type of a domain model property is changed. The change is displayed  
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)  
  /// </summary>  
  [RuleOn(typeof(PropertyHasType))]  
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule  
  {  
    /// <summary>  
    /// Method called when the Type of a Domain Property   
    /// is changed by the user in a DslDefinition  
    /// </summary>  
    /// <param name="e"></param>  
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)  
    {  
      // We are only interested in the type  
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)  
      {  
        PropertyHasType relationship =   
           e.ElementLink as PropertyHasType;  
        DomainType newType = e.NewRolePlayer as DomainType;  
        DomainType oldType = e.OldRolePlayer as DomainType;  
        DomainProperty property = relationship.Property;  
  
         // We write about the Type change in the debugguer  
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",  
          property.Name,  
          property.Class.Name,  
          oldType.GetFullName(false),  
          newType.GetFullName(false))  
} }  }  );  
```  
  
 Следующий код реализует простую модель. Создайте новый идентификатор GUID для замены заполнителя.  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
    /// <summary>  
    /// Simplest possible domain model   
    /// needed only for extension rules.   
    /// </summary>  
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]  
    public class SimpleDomainModelExtension : DomainModel  
    {  
        // Id of this domain model extension   
        // Please replace this with a new GUID:  
        public const string DomainModelId =   
                  "00000000-0000-0000-0000-000000000000";  
  
        /// <summary>  
        /// Constructor for the domain model extension  
        /// </summary>  
        /// <param name="store">Store in which the domain model will be loaded</param>  
        public SimpleDomainModelExtension(Store store)  
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))  
        {  
  
        }  
  
        /// <summary>  
        /// Rules brought by this domain model extension  
        /// </summary>  
        /// <returns></returns>  
        protected override System.Type[] GetCustomDomainModelTypes()  
        {  
            return new Type[] {  
                     typeof(DomainPropertyTypeChangedRule)  
                              };  
        }  
    }  
  
    /// <summary>  
    /// Provider for the DomainModelExtension  
    /// </summary>  
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]  
    public class SimpleDomainModelExtensionProvider   
          : DomainModelExtensionProvider  
    {  
        /// <summary>  
        /// Extension model type  
        /// </summary>  
        public override Type DomainModelType  
        {  
            get  
            {  
                return typeof(SimpleDomainModelExtension);  
            }  
        }  
  
    }  
}  
```
