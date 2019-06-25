---
title: Языковые службы и базовый редактор | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a27fc9ec55b301dc3355e03e2e86e968752fbbd0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309538"
---
# <a name="language-services-and-the-core-editor"></a>Языковые службы и базовым редактором
Редакторы в среде Visual Studio часто связаны с языковой службой. Помимо прочего языковая служба предоставляет Цветовая подсветка синтаксиса, завершение операторов, IntelliSense и форматированием текста.

## <a name="core-editors-and-document-data-objects"></a>Редакторы Core и объектов данных документа
 При доступе к базовым редактором, не следует создавать данные документа и объекты представления документа. Среда IDE создает и управляет этими двумя объектами, и получить маркеры, чтобы их, выполнив соответствующие вызовы реализацию фабрики редактора.

 Дополнительные сведения см. в разделе [определить, какой редактор открывает файл в проекте](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).

## <a name="language-services-and-the-core-editor"></a>Языковые службы и базовым редактором
 Путем реализации языковой службы, можно управлять отображением данных в представление документа. Служба языка предоставляет информацию и поведение, характерное для данного языка, например Visual C++. При создании текстового буфера и определить расширение имени файла для документа, открытии, текстовый буфер определяет языковой службы, связанный с расширением имени файла из раздела реестра, **HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\Editors\\\Extensions {YourLanguageService GUID}** . Стандартный пакет VSPackage, загрузка процедура затем загружает VSPackage и создается экземпляр службы языка.

 На следующем рисунке показан базовый языковой службы.

 ![График языка модели службы](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") базовые объекты, редактора и языковой службы

 Объект данных документа для базового редактора называется текстового буфера, а также представлен <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объекта. Объект представления документа называется представлением текста, а также представлен <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> объекта. Эти два объекта совместной работы через языковой службы для предоставления унифицированного представления базовым редактором. Сведения из текстового буфера и отображает представление текста в окне документа вызывается окна кода. Окно документа кода управляет диспетчер окон кода.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>
- [Предоставить контекст службы языка с помощью предыдущих версий API](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)
- [Размещение IntelliSense](../extensibility/intellisense-hosting.md)
- [Содержащихся языков](../extensibility/contained-languages.md)
- [Разработка языковой службы прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)