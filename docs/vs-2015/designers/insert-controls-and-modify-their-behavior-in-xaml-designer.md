---
title: Вставка элементов управления и изменение их поведения в конструкторе XAML | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e36b7cef0c24367292f7f9e60b86eb9138b12a64
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159487"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Вставка элементов управления и изменение их поведения в конструкторе XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Элементы управления позволяют пользователям взаимодействовать с приложением. Их можно использовать для сбора сведений и выполнения таких действий, как анимация объекта или отправка запроса к источнику данных.  
  
 **В этом разделе:**  
  
- [Добавление элементов управления в область рисования](#Insert)  
  
- [Настройка элементов управления для выполнения различных действий](#Modify)  
  
## <a name="Insert"></a> Добавление элементов управления в область рисования  
 Вы можете перетащить элементы управления из панели **Ресурсы** в **область рисования**, а затем изменить их в окне **Свойства** .  
  
 ![Blend & #45; Ресурсы & #45; FlipView](../designers/media/blend-assetsflipview-xaml.png "blend_AssetsFlipView_XAML")  
  
 В этом видео показано, как использовать некоторые из наиболее часто используемых элементов управления.  
  
|Элемент управления|Ознакомьтесь с коротким видео.|  
|-------------|-------------------------|  
|`Menu` ![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c-0b2b-4253-ac57-b86fcb8c9591")|![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Добавление элементов управления](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|  
|`Button` ![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779-a68f-436b-b834-a91b7995a3ec")|![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Проектирование кнопки](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|  
|`Textblock` ![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963-00f7-4a33-abcd-b0849edebada")|![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Добавление изображений в блок текста](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|  
|`Slider` ![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92-3c74-4218-815c-e98c930ac189")|![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Создание ползунка с подсказкой](http://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|  
|`GridSplitter` ![](../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be")|![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Работа с GridSplitter](https://www.youtube.com/watch?v=bf4t6c8ms2w)|          

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Создание элемента управления из изображения, фигуры или контура  
 Любой объект можно преобразовать в элемент управления.  
  
 ![Диалоговое окно "Преобразование в элемент управления" в Blend](../designers/media/blend-makeintocontrol-xaml.png "blend_MakeIntoControl_XAML")  
  
 Например, представьте в центре страницы изображение телевизора. Элементы управления можно создать из изображений небольшого размера, которые выглядят как кнопки телевизора. Впоследствии пользователи смогут нажимать эти кнопки для смены каналов.  
  
 Это возможно, поскольку кнопки теперь являются элементами управления. С помощью элементов управления можно управлять взаимодействием с пользователем; в данном случае это происходит, когда пользователь нажимает кнопку.  
  
 Чтобы создать элемент управления, выберите объект. Затем в меню **Средства** выберите пункт **Создать элемент управления**.  
  
## <a name="Modify"></a> Настройка элементов управления для выполнения различных действий  
 Элементы управления могут выполнять действия, когда пользователи используют их. Например, они могут запустить анимацию, обновить источник данных или воспроизвести видео.  
  
 Используйте *триггеры*, *поведения*и *события* , чтобы настроить элементы управления для выполнения действий.  
  
### <a name="triggers"></a>триггеры  
 *Триггер* изменяет свойство или выполняет задачу в ответ на событие или изменение другого свойства. Например, цвет кнопки может измениться при наведении на нее курсора.  
  
 ![Панель “Триггеры”](../designers/media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Добавление триггера свойства](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).  
  
### <a name="behaviors"></a>поведения  
 *Поведение* — это повторно используемый пакет кода. Этот объект включает дополнительные возможности помимо изменения свойств. Этот объект может выполнять такие действия, как отправка запроса в службу данных. Blend поставляется с небольшим числом таких объектов, но впоследствии вы можете добавить дополнительные объекты. Перетащите поведение для любого объекта в области рисования, а затем настройте поведение, задав свойства.  
  
 ![FluidMoveBehavior на панели "Свойства"](../designers/media/b4-fluidmovebehaviorproperties-sample.png "b4_FluidMoveBehaviorProperties_Sample")  
  
 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [советы по Blend: введение в использование поведений, часть 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).  
  
### <a name="events"></a>События  
 Для обеспечения наибольшей эффективности необходимо использовать *событие*. Для этого необходимо написать код.  
  
 **Ознакомьтесь с коротким видео.** ![Настройка установленных компонентов](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Добавление события мыши](https://www.youtube.com/watch?v=2PMxAlb-x_E).
