---
title: Упрощенное внедрение | Документация Майкрософт
description: Сведения о упрощенном внедрении, которое можно включить в редакторе, если его объект представления документа является дочерним по отношению к Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99aaf5070646bbbb95c6be98eb8ac2f7a5948ff2
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715279"
---
# <a name="simplified-embedding"></a>Упрощенное внедрение
Упрощенное внедрение в редакторе включается, если его объект представления документа является родительским для (то есть дочерним элементом) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , а <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс реализуется для обработки его команд окна. Упрощенные редакторы внедрений не могут размещать активные элементы управления. На следующем рисунке показаны объекты, используемые для создания редактора с упрощенным внедрением.

 ![Упрощенное изображение редактора внедрений](../extensibility/media/vssimplifiedembeddingeditor.gif "вссимплифиедембеддинжедитор") Редактор с упрощенным внедрением

> [!NOTE]
> Из объектов на этом рисунке `CYourEditorFactory` для создания стандартного редактора на основе файлов требуется только объект. При создании пользовательского редактора не требуется реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> , так как в редакторе, скорее всего, будет собственный частный механизм сохранения. Однако для непользовательских редакторов это необходимо.

 Все интерфейсы, реализованные для создания редактора с упрощенным внедрением, содержатся в `CYourEditorDocument` объекте. Однако для поддержки нескольких представлений данных документа разделите интерфейсы на отдельные данные и объекты представления, как показано в следующей таблице.

|Интерфейс|Расположение интерфейса|Использовать|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Представление|Обеспечивает подключение к родительскому окну.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Представление|Обрабатывает команды.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Представление|Обеспечивает обновление строки состояния.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Представление|Включает элементы **панели элементов** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Данные|Отправляет уведомления при изменении файла.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Данные|Включает функцию "Сохранить как" для типа файлов.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Данные|Обеспечивает сохраняемость документа.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Данные|Позволяет подавлять события изменения файлов, такие как запуск повторной загрузки.|
