---
title: Объект Встекстбуффер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 193d96be91839143893ac0798db723f3e94ea26c
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2020
ms.locfileid: "93413920"
---
# <a name="vstextbuffer-object"></a>Объект Встекстбуффер
Объект текстового буфера представляет поток текста в Юникоде, который обычно связан с файлом. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>Объект может использоваться вне контекста основного редактора, как в мастере.

 В следующей таблице показаны интерфейсы `VSTextBuffer` .

|Метод|Описание|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Стандартный OLE-интерфейс. Используется для обработки операций отмены или повтора в буфере.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Стандартный OLE-интерфейс.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Стандартный OLE-интерфейс.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Включает создание составных действий (то есть действий, сгруппированных в одну единицу отмены или повтора).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Включает сохранение данных документа, управляемого с помощью текстового буфера.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Предоставляет базовые службы. используется многими клиентами.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Используется для поиска в буфере.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Предоставляет возможности чтения и записи с помощью двумерных координат. Наследует от `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Предоставляет возможности чтения и записи, используя одномерные координаты. Наследует от `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Обеспечивает быстрый, ориентированный на поток последовательный доступ к тексту в буфере.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Предоставляет доступ к универсальной коллекции свойств. Наиболее важным свойством является имя или моникер буфера. Вы можете хранить собственные случайные данные в буфере с помощью этого интерфейса, создавая GUID и используя его в качестве ключа.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Поддерживает точки соединения для событий.|

## <a name="remarks"></a>Комментарии
 `VSTextBuffer`Обычно обнаруживается `QueryInterface` вызовом в `IVsTextBuffer` . Дополнительные сведения см. в разделе [текстовый буфер](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Изменение фигур](https://www.microsoft.com/download/details.aspx?id=55984)