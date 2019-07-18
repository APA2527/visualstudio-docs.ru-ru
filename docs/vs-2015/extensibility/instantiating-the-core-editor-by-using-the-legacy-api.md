---
title: Создание экземпляра базового редактора с помощью API прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29306a16390039c8ee6e424b81a5ff617e533ab4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203910"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Создание экземпляра основного редактора с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Редактор несет ответственность за изменения функции, такие как вставки, удаления, копирования и вставки текста. Оно объединяет эти функции с образы, предоставляемые службы языка, такие как выделение цветом текста, отступы и завершение операторов IntelliSense.  
  
 Можно создать экземпляр базовым редактором в одном из трех способов:  
  
- Явно создайте экземпляр ядра редактора в окне.  
  
- Предоставить фабрику редактора, который возвращает экземпляр базового редактора  
  
- Откройте файл из иерархии проекта.  
  
  В следующих разделах рассматриваются способы использования старый API для создания экземпляра редактора.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Явно открытия экземпляра базового редактора  
 Получив явно экземпляр базового редактора:  
  
- Получить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> для размещения редактируемого объекта данных документа.  
  
- Создайте представление объекта данных документа в строке, ориентированной путем создания <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> интерфейс из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> интерфейс.  
  
- Задайте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> как объект данных документа для экземпляра по умолчанию реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> интерфейс, с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> метод.  
  
   Узел <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> в экземпляре <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> интерфейса с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> метод.  
  
  На этом этапе отображение <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> интерфейс предоставляет окно, которое содержит экземпляр базового редактора.  
  
  Тем не менее это не очень полезный экземпляр, так как она не имеют сочетания клавиш, или доступ к расширенным функциям. Чтобы получить доступ к сочетания клавиш, а также дополнительные возможности:  
  
- Использование <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> метода, чтобы установить языковой службы и объект данных документа, который используется в редакторе.  
  
- Создать сочетания клавиш, или использовать системное значение по умолчанию, задав <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объекты отображаются свойства. Чтобы сделать это, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> метод с <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> свойство.  
  
   Чтобы получить и использовать нестандартные сочетания клавиш, создайте их с помощью файла .vsct. Дополнительные сведения см. в разделе [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Как использовать фабрику редактора для получения базового редактора  
 При реализации базового редактора с помощью редактора фабрики с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод, выполните все шаги, описанные в предыдущем разделе, чтобы явным образом разместить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> объект данных документа, в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объекта.  
  
 Для отображения текста, получить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейс из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> и вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод.  
  
 Чтобы предоставить службе языка редактор, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> метода в <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод.  
  
 Для получения по умолчанию сочетания клавиш, в отличие от предыдущего раздела, используйте команду контекста, возвращаемого свойством <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод при получении базового редактора из <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод.  
  
 Если <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод возвращает ту же команду GUID как текстовый редактор, экземпляр базового редактора автоматически получает значение по умолчанию сочетания клавиш.  
  
 Общие сведения см. в разделе [Пошаговое руководство: Создание базового редактора и регистрация файла тип редактора](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>См. также  
 [В редакторе](../extensibility/inside-the-core-editor.md)   
 [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md)   
 [Пошаговое руководство: создание основного редактора и регистрация типов файлов в редакторе](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
