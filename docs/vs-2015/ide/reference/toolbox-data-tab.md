---
title: Панель элементов, вкладка "Данные" | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Data tab
- Data tab, Toolbox
- data [Visual Studio], Toolbox
ms.assetid: 2ae38b2a-29d2-461c-a67d-29dad274bf45
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9349745eeee24f2f8b1e62eb2b01bd75273c86d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658587"
---
# <a name="toolbox-data-tab"></a>Панель элементов, вкладка "Данные"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отображение объектов данных, которые можно добавлять в формы и компоненты. Вкладка **Данные** **панели элементов** появляется при создании проекта, для которого есть связанный конструктор. **Панель элементов** по умолчанию отображается в интегрированной среде разработки Visual Studio; чтобы открыть **панель элементов**, выберите в меню **Вид** пункт **Панель элементов**.

> [!TIP]
> Запуск мастера настройки источников данных позволяет автоматически создать и настроить большинство элементов данных. Дополнительные сведения см. в статье [Creating Data Applications with Visual Studio](https://msdn.microsoft.com/28edce21-220a-484c-b461-a75b0232d293) (Создание приложений данных с помощью Visual Studio).

## <a name="ui-element-list"></a>Список элементов пользовательского интерфейса
 Чтобы перейти непосредственно на страницу справочника по .NET Framework для конкретного компонента, нажмите клавишу **F1** для элемента на **панели элементов** или для элемента компонента в области конструктора.

|Имя|Description|
|----------|-----------------|
|<xref:System.Data.DataSet>|Добавляет экземпляр типизированного или нетипизированного набора данных в форму или компонент. При перетаскивании объекта в конструктор отображается диалоговое окно, которое позволяет выбрать существующий класс типизированного набора данных или указать, что требуется создать новый, пустой, нетипизированный набор данных. **Примечание**. Объект <xref:System.Data.DataSet> не используется на **панели элементов** для создания новой схемы и класса типизированного набора данных. Дополнительные сведения см. в разделе, посвященном [созданию и настройке наборов данных](../../data-tools/create-and-configure-datasets-in-visual-studio.md).|
|<xref:System.Windows.Forms.DataGridView>|Обеспечивает эффективный и гибкий способ отображения данных в табличном формате.|
|<xref:System.Windows.Forms.BindingSource>|Упрощает процесс привязки элементов управления к базовому источнику данных.|
|<xref:System.Windows.Forms.BindingNavigator>|Представляет пользовательский интерфейс для перехода и обработки для элементов управления в форме, которые привязываются к данным.|

## <a name="see-also"></a>См. также:
 [Пошаговые руководства](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) [по данным привязывают Windows Forms элементы управления к данным в Visual Studio](../../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [Подготовка приложения к получению](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [элементов управления привязки данных в данных в Visual Studio](../../data-tools/bind-controls-to-data-in-visual-studio.md) [Проверка данных](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)