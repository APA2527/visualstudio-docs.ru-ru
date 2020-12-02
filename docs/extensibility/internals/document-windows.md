---
title: Окна документов | Документация Майкрософт
description: Сведения о окнах документов в Visual Studio, в том числе о способах их реализации и о том, как выполняемая таблица документов (РДТ) отслеживает свое состояние.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f39c02ece35a36ceb763a2a5b84f8431043a1b50
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480009"
---
# <a name="document-windows"></a>Окна документов
В Visual Studio *окно документа* является дочерним окном с фреймами, связанным с окном многодокументного интерфейса (MDI). Окна документов обычно используются для просмотра и изменения исходного кода или текста, но они также могут содержать другие функциональные типы. Окна документов:

- Можно организовать в отдельные группы горизонтальных или вертикальных вкладок в родительском интерфейсе MDI, чтобы одновременно просматривать несколько файлов.

- Может закрепляться в любом порядке в родительском интерфейсе MDI.

- Может быть свободно плавающей.

- Связаны в порядке табуляции с другими окнами MDI.

  Команды для группирования, закрепления и плавающего типа можно найти в контекстном меню на вкладке окна документа.

  Дополнительные сведения о поведении окон в Visual Studio см. в разделе [Настройка макетов окон](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Реализация окна документа
 Окна документов создаются путем реализации редактора. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>Интерфейс создает окна документов в процессе создания экземпляра редактора. Дополнительные сведения см. [в разделе устаревшие интерфейсы в редакторе](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015).

> [!NOTE]
> Чтобы обеспечить обратную и прямую точку навигации в окне, реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> интерфейс. Текстовый редактор использует текстовые маркеры для обнаружения точек перехода в документе.

## <a name="the-running-document-table"></a>Таблица выполняющегося документа
 Интегрированная среда разработки использует таблицу выполняемых документов (РДТ) для наблюдения за состоянием каждого окна документа. РДТ — это механизм, с помощью которого окна документов получают уведомления о событиях, например о закрытии решения или изменении файла. Дополнительные сведения см. в разделе [выполнение таблицы документов](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>См. также раздел
- [Отложенная загрузка документов](../../extensibility/internals/delayed-document-loading.md)
