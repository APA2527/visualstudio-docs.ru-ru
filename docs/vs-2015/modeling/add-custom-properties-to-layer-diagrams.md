---
title: Добавление пользовательских свойств в схемы слоев | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom properties
ms.assetid: 52b3ac25-d10b-4507-a1fe-209ccb4d2777
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 75d3284c4584c67550c7dcee3c8f1737ebed5380
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871919"
---
# <a name="add-custom-properties-to-layer-diagrams"></a>Добавление пользовательских свойств в схемы слоев
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При написании кода расширения для схем слоев можно хранить значения в любом элементе на схеме слоев. Значения сохраняются при сохранении и повторном открытии схемы. Эти свойства также можно отобразить в окне **Свойства** , чтобы пользователи могли просматривать и изменять их. Например, можно позволить пользователям задать регулярное выражение для каждого слоя и написать код для проверки того, соответствуют ли имена классов в каждом слое шаблону, заданному пользователем.

## <a name="properties-not-visible-to-the-user"></a>Свойства, не видимые пользователю
 Если код должен просто связывать значения с любым элементом на схеме слоев, определять компонент MEF не нужно. В [ILayerElement](/previous-versions/ff644511(v=vs.140)) есть словарь с именем `Properties`. Просто добавьте маршалируемые значения в словарь любого элемента слоя. Они будут сохранены вместе со схемой слоев. Дополнительные сведения см. [в разделе Навигация и обновление моделей слоев в коде программы](../modeling/navigate-and-update-layer-models-in-program-code.md).

## <a name="properties-that-the-user-can-edit"></a>Свойства, которые пользователь может изменять
 **Начальная подготовка**

> [!IMPORTANT]
> Чтобы свойства отображались, нужно внести описанное ниже изменение на каждом компьютере, на котором свойства слоев должны быть видимыми.
>
>  1. Запустите Блокнот с помощью команды **Запуск от имени администратора**. Откройте файл `%ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest`.
>
>  2. Внутри элемента `Content` добавьте следующую запись:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
>  3. В разделе **инструменты Visual Studio** меню Пуск приложения Visual Studio откройте **Командная строка разработчика**.
>
>     Введите следующие команды:
>
>     `devenv /rootSuffix /updateConfiguration`
>
>     `devenv /rootSuffix Exp /updateConfiguration`
>
>  4. Перезапустите Visual Studio.

 **Убедитесь, что код находится в проекте VSIX**

 Если свойство является частью команды, жеста или проекта проверки, ничего добавлять не нужно. Код пользовательского свойства должен быть определен в проекте расширения Visual Studio как компонент MEF. Дополнительные сведения см. в статьях [Добавление команд и жестов в схемы слоев](../modeling/add-commands-and-gestures-to-layer-diagrams.md) или [Добавление пользовательской проверки архитектуры в схемы слоев](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

 **Определение пользовательского свойства**

 Чтобы создать пользовательское свойство, определите класс, как показано ниже.

```
[Export(typeof(IPropertyExtension))]
public class MyProperty
      : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

 Можно определить свойства для [илайерелемент](/previous-versions/ff644511(v=vs.140)) или любого из его производных классов, которые включают:

- `ILayerModel` — модель

- `ILayer` — каждый слой

- `ILayerDependencyLink` — ссылки между слоями

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>Пример
 Приведенный ниже код представляет собой типичный дескриптор пользовательского свойства. Он определяет логическое свойство в модели слоев (`ILayerModel`), которое позволяет пользователю предоставлять значения для пользовательского метода проверки.

```
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;

namespace MyNamespace
{
  /// <summary>
  /// Custom properties are added to the Layer Designer via a custom
  /// Property Descriptor. We have to export this Property Descriptor
  /// using MEF to make it available in the Layer Designer.
  /// </summary>
  [Export(typeof(IPropertyExtension))]
  public class AllTypesMustBeReferencedProperty
      : PropertyExtension<ILayerModel>
  {
    /// <summary>
    /// Each custom property must have a unique name.
    /// Usually we use the full name of this class.
    /// </summary>
    public static readonly string FullName =
      typeof(AllTypesMustBeReferencedProperty).FullName;

    /// <summary>
    /// Construct the property. Notice the use of FullName.
    /// </summary>
    public AllTypesMustBeReferencedProperty()
            : base(FullName)
    {  }

    /// <summary>
    /// The display name is shown in the Properties window.
    /// We therefore use a localizable resource.
    /// </summary>
    public override string DisplayName
    {
      get { return Strings.AllTypesMustBeReferencedDisplayName; }
    }

    /// <summary>
    /// Description shown at the bottom of the Properties window.
    /// We use a resource string for easier localization.
    /// </summary>
    public override string Description
    {
      get { return Strings.AllTypesMustBeReferencedDescription; }
    }

    /// <summary>
    /// This is called to set a new value for this property. We must
    /// throw an exception if the value is invalid.
    /// </summary>
    /// <param name="component">The target ILayerElement</param>
    /// <param name="value">The new value</param>
    public override void SetValue(object component, object value)
    {
      ValidateValue(value);
      base.SetValue(component, value);
    }
    /// <summary>
    /// Helper to validate the value.
    /// </summary>
    /// <param name="value">The value to validate</param>
    private static void ValidateValue(object value)
    {  }

    public override Type PropertyType
    { get { return typeof(bool); } }

    /// <summary>
    /// The segment label of the properties window.
    /// </summary>
    public override string Category
    {
      get
      {
        return Strings.AllTypesMustBeReferencedCategory;
      }
    }
  }
}
```

## <a name="see-also"></a>См. также
 [Расширение схем слоев](../modeling/extend-layer-diagrams.md)
