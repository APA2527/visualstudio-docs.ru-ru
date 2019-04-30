---
title: Объект VSTextView | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab54fce0271438f89ec66b4fc5d8db1ebe21634f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953092"
---
# <a name="vstextview-object"></a>Объект VSTextView
Представление текста — это окно, которое позволяет пользователям просматривать и редактировать текст в Юникоде текстового буфера. По сути это представление является то, что большинство пользователей называть редактора. Так как представление отделяется различные уровни текста (перенос по словам, структуры текста и т. д.) из буфера, представление не гарантированно точное представление текста в буфере. Дополнительные сведения о представлении текста см. в разделе [доступ к theText представление с использованием предыдущих версий API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

 В следующей таблице показаны интерфейсы <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объекта.

|Интерфейс|Описание|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Стандартный OLE-интерфейс.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Стандартный OLE-интерфейс.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Стандартный OLE-интерфейс.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Стандартный OLE-интерфейс.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Разрешает создание составных действий (то есть действия, которые группируются в единое единый отмены и повтора).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Предоставляет основные методы для управления и доступ к представлению. `IVsTextView` не является однопоточным safe.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Создает и управляет область окна.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Взаимодействует с уровнями текста.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Выполняет операции на представлении из другого потока.|

## <a name="see-also"></a>См. также
- [Изменение фигур](https://www.microsoft.com/download/details.aspx?id=55984)
- [Объект VSTextBuffer](../extensibility/vstextbuffer-object.md)
- [Доступ к theText представления с помощью предыдущих версий API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)