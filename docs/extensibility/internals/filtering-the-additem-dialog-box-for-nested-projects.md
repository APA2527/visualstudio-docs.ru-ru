---
title: Фильтрация диалогового окна AddItem для вложенных проектов | Документация Майкрософт
description: Узнайте, как отфильтровать диалоговое окно AddItem для вложенного проекта в Visual Studio, реализовав интерфейс Ивсфилтераддпрожектитемдлг родительского проекта.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02d574007250960e3cb0b39bf50696f03af98e27
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480465"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Фильтрация диалогового окна AddItem для вложенных проектов
При отображении диалогового окна **AddItem** для вложенного проекта родительский проект может управлять тем, какие элементы отображаются в диалоговом окне.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>Интерфейс позволяет фильтровать узлы, которые будут находиться в диалоговом окне **AddItem** . Когда в дочернем проекте отображается диалоговое окно **AddItem** , родительский проект может реализовать `IVsFilterAddProjectItemDlg` интерфейс и фильтровать элементы, которые в противном случае будут отображаться в проекте дочернего проекта.

 Если проекты группируются по функциям в конкретных родительских проектах, можно реализовать, `IVsFilterAddProjectItemDlg` когда пользователь выбирает пункт **Добавить проект** в контекстном меню вложенного проекта. Реализация `IvsFilterAddProjectItemDlg displays` только элементов проекта или файлов, относящихся к этой группе. Элементы проекта для других групп отфильтровываются из диалогового окна, даже если они хранятся в одном и том же каталоге.

 Когда пользователь открывает диалоговое окно **AddItem** для дочернего элемента, вызывается реализация интерфейса для родительского проекта `IVsFilterAddProjectItemDlg` .

 `IVsFilterAddProjectItemDlg`Интерфейс также может реализовывать фильтрацию по категории. Дополнительные сведения см. в разделе [Добавление элементов в диалоговое окно "Добавление нового элемента"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) и [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>См. также раздел
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Добавление элементов в диалоговое окно "Добавление нового элемента"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)
- [Вложенные проекты](../../extensibility/internals/nesting-projects.md)
