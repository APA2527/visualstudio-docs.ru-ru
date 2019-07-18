---
title: Кнопки окна свойств | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b66015ef2e2ab0c8105b6f84486fa890adbf8b1f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438395"
---
# <a name="properties-window-buttons"></a>Кнопки окна свойств
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В зависимости от языка разработки и тип продукта, по умолчанию на панели инструментов отображаются определенные кнопки **свойства** окна. Во всех случаях **по категориям**, **Alphabetized**, **свойства**, и **страницы свойств** отображаются кнопки. В Visual C# и Visual Basic **события** также отображается кнопка ". В некоторых проектах Visual C++ **сообщения VC ++** и **переопределяет VC** отображаются кнопки. Дополнительные кнопки может отображаться для других типов проектов. Дополнительные сведения о кнопках в **свойства** окно, см. в разделе [окно "Свойства"](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Реализация кнопки окна свойств  
 При нажатии кнопки **по категориям** кнопку, Visual Studio вызывает <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> интерфейс объекта, имеющего фокус, чтобы отсортировать его свойства по категориям. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> реализуется на `IDispatch` объект, который представляется **свойства** окна.  
  
 Существует 11 предопределенное свойство категории, которые имеют отрицательные значения. Можно определить пользовательские категории, но мы рекомендуем назначить их положительные значения, чтобы отличать их от стандартных категорий.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> Метод возвращает значение соответствующего свойства категории для указанного свойства. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> Метод возвращает строку, содержащую имя категории. Достаточно для обеспечения поддержки пользовательской категории значений, так как Visual Studio поддерживает стандартные категории значения свойств.  
  
 При нажатии кнопки **Alphabetized** кнопку, свойства отображаются в алфавитном порядке по имени. Имена извлекаются путем `IDispatch` в соответствии с локализованной алгоритм сортировки.  
  
 Когда **свойства** открыто окно, **свойства** кнопка автоматически отображается как выбранный. В других частях среды отображается та же кнопка, и можно щелкнуть его, чтобы отобразить **свойства** окна.  
  
 **Страницы свойств** недоступна при `ISpecifyPropertyPages` не реализован для выбранного объекта. Отображение свойств зависимых от конфигурации, которые обычно связаны с решениями и проектами страницы свойств, но они могут быть также быть связаны с элементами проекта (например, в Visual C++).  
  
> [!NOTE]
> Не удается добавить кнопки панели инструментов для **свойства** окна с помощью неуправляемого кода. Чтобы добавить кнопку панели инструментов, необходимо создать управляемый объект, производный от <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## <a name="see-also"></a>См. также  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)
