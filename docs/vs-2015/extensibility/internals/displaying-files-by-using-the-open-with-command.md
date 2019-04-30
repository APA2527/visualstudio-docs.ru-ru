---
title: Отображение файлов с помощью открыть с помощью команды | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de43b6c4f441f8c6bde2d6c248274aed3937a7ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408810"
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Отображение файлов с помощью команды "Открыть с помощью"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Проект можно попросить интегрированной среды разработки для отображения **открыть с помощью** диалоговое окно. Этот запрос предлагает пользователю открыть файл, который включает набор стандартных редакторов. Следующие шаги описывают этот процесс.  
  
1. Вызовы проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, указав значение OSE_UseOpenWithDialog для `OSEOpenDocEditor` параметра.  
  
2. Исходя из расширение имени файла документа, интегрированной среды разработки определяет, какие редакторы, перечисленных в реестре может открыть указанный документ и отображает эти сведения в **открыть с помощью** диалоговое окно.  
  
    > [!NOTE]
    > Проекты, которые имеют встроенный редактор, который должен быть включен в **открыть с помощью** диалоговое окно необходимо зарегистрировать фабрику редактора для каждого такого редактора. Встроенные редакторы работают только вместе с определенного типа проекта, который применяется в реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод. В среде IDE существует фабрику встроенного редактора для базовый текстовый редактор и двоичный редактор. Интегрированной среды разработки также создает экземпляр фабрики редактора, от имени каждого зарегистрированного сопоставления файлов Windows. Пример такого файла — Microsoft Word.  
  
3. Как только пользователь выбирает элемент из **открыть с помощью** диалоговом окне интегрированной среды разработки затем открывает документ, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод. Дополнительные сведения см. в разделе [Как Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>См. также  
 [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Отображение файлов с помощью команды открытия файла](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Практическое руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)
