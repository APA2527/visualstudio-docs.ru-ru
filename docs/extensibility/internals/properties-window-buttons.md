---
title: Кнопки окна "Свойства" | Документация Майкрософт
description: Сведения о кнопках, отображаемых по умолчанию на панели инструментов для окно свойств и о реализации кнопок.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e99c362904bc40a2937c030f1ee2bb1c4d32a113
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2021
ms.locfileid: "97878018"
---
# <a name="properties-window-buttons"></a>Кнопки окна свойств
В зависимости от языка разработки и типа продукта определенные кнопки по умолчанию отображаются на панели инструментов окна « **Свойства** ». Во всех случаях отображаются кнопки **категории**, по **алфавиту**, **Свойства** и **страницы свойств** . В Visual C# и Visual Basic также отображается кнопка **события** . В некоторых Visual C++ проектах отображаются **сообщения VC + +** и кнопки **переопределения VC** . Для других типов проектов могут отображаться дополнительные кнопки. Дополнительные сведения о кнопках в окне " **Свойства** " см. в разделе " [окно свойств](../../ide/reference/properties-window.md)".

## <a name="implementation-of-properties-window-buttons"></a>Реализация кнопок окна свойств
 При нажатии кнопки по **категориям** Visual Studio вызывает <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> интерфейс для объекта, который имеет фокус на сортировку его свойств по категориям. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> реализуется для `IDispatch` объекта, представленного в окне **свойства** .

 Существует 11 предопределенных категорий свойств, имеющих отрицательные значения. Можно определить пользовательские категории, но рекомендуется назначить их положительные значения, чтобы отличать их от стандартных категорий.

 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A>Метод возвращает соответствующее значение категории свойств для указанного свойства. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A>Метод возвращает строку, содержащую имя категории. Необходимо предоставить поддержку для значений пользовательских категорий, так как Visual Studio знает значения стандартных категорий свойств.

 При нажатии кнопки по **алфавиту** свойства отображаются в алфавитном порядке по имени. Имена извлекаются в `IDispatch` соответствии с локализованным алгоритмом сортировки.

 Когда окно **свойств** открыто, кнопка **свойства** автоматически отображается как выбранная. В других частях среды отображается одна и та же кнопка, и вы можете щелкнуть ее, чтобы открыть окно **Свойства** .

 Кнопка **страницы свойств** недоступна, если `ISpecifyPropertyPages` для выбранного объекта не реализована. Страницы свойств отображают зависящие от конфигурации свойства, которые обычно связаны с решениями и проектами, но их также можно связать с элементами проекта (например, в Visual C++).

> [!NOTE]
> Нельзя добавить кнопки панели инструментов в окно **свойств** с помощью неуправляемого кода. Чтобы добавить кнопку на панели инструментов, необходимо создать управляемый объект, производный от <xref:System.Windows.Forms.Design.PropertyTab> .

## <a name="see-also"></a>См. также раздел
- [Расширение свойств](../../extensibility/internals/extending-properties.md)
