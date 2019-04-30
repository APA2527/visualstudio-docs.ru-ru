---
title: Практическое руководство. Открытие стандартных редакторов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f34a239628c3ed9e8bccaa8590cb22100d7d290f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62862918"
---
# <a name="how-to-open-standard-editors"></a>Практическое руководство. Стандартные редакторы
При открытии стандартного редактора, позволить определить стандартный редактор для назначенного типа файлов, вместо указания проектного редактора для файла интегрированной среды разработки.

 Выполните следующую процедуру для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> метод. Файл проекта откроется в стандартный редактор.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Чтобы реализовать метод OpenItem с помощью стандартного редактора

1. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> (`RDT_EditLock`) для определения ли файл объекта данных документа уже открыт.

2. Если файл уже открыт, resurface файл путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> метод, указывая значение `IDO_ActivateIfOpen` для `grfIDO` параметра.

     Если файл открыт и принадлежит другому проекту чем вызывающего проекта документа, ваш проект получает предупреждение, что редактор открывается из другого проекта. Затем отображается окно файла.

3. Если документ не открыт или не в таблице выполняющихся документов, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод (`OSE_ChooseBestStdEditor`) для открытия стандартного редактора для файла.

     При вызове метода, интегрированная среда разработки выполняет следующие задачи:

    1. Интегрированной среды разработки сканирует редакторов / {guidEditorType} / расширения раздел реестра, чтобы определить, какой редактор можно открыть файл и имеет наивысший приоритет для этого.

    2. После интегрированной среды разработки определяет, какой редактор можно открыть файл, интегрированной среды разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. Реализация редактора, этот метод возвращает сведения, которые требуются для интегрированной среды разработки для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> и сайта открытый документ.

    3. Наконец, интегрированной среды разработки загружает документ в интерфейсе обычные сохраняемости, такие как <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.

    4. Если ранее определено интегрированной среды разработки, что иерархия или элемент иерархии доступен, интегрированной среды разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> метод в проекте для получения контекста на уровне проекта <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> указатель для передачи обратно с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> вызова метода.

4. Вернуть <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> указатель в интегрированную среду разработки, когда вызывает интегрированной среды разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> в проекте, если вы хотите разрешить контекст get редактора из проекта.

     Выполнение этого действия позволяет проекта предложения дополнительных служб в редактор.

     Если представление документа или объекта представления документа был успешно помещен в узел в рамку окна, объект инициализируется с его данными путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md)
- [Практическое руководство. Открытие редакторов соответствующих проектов](../extensibility/how-to-open-project-specific-editors.md)
- [Практическое руководство. Открытие редакторов для открытых документов](../extensibility/how-to-open-editors-for-open-documents.md)
- [Отображение файлов с помощью команды открытия файла](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)