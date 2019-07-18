---
title: Константы среды IDE | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 18256996d829d34117caa11f4e581d8e54d738b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204038"
---
# <a name="ide-constants"></a>Константы среды IDE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.VisualStudio.VSConstants> Класс предоставляет константы, которые относятся к интегрированной среде разработки (IDE), были ранее определены только в файлах заголовков.  
  
## <a name="logical-and-physical-views"></a>Логические и физические представления.  
  
|Значение|Описание|  
|-----------|-----------------|  
|[LOGVIEWID_Code_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.code_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики должны передавать это значение <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод для получения **открыть с помощью** диалоговое окно, в данном случае с возможными представлениями кода.|  
|[LOGVIEWID_Debugging_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.debugging_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики передавать это значение <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод для получения **открыть с помощью** диалоговое окно, в данном случае заполненного возможными <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> отладки представления, которые сопоставляются с тем же самым представлением как <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|  
|[LOGVIEWID_Designer_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.designer_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики передавать это значение <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод для получения **открыть с помощью** диалоговое окно, в этом случае для **форма просмотра** представления конструктора.|  
|[LOGVIEWID_Primary_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.primary_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики передавать это значение <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод для получения **открыть с помощью** диалоговое окно, в нашем примере это представление по умолчанию источник фабрики редактора.|  
|[LOGVIEWID_TextView_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.textview_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики передавать это значение <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод для получения **открыть с помощью** диалоговое окно, в данном случае для документа или данных представление текстового редактора.|  
|[LOGVIEWID_UserChooseView_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.userchooseview_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики передавать это значение <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, который предлагает пользователю выбрать определяемые пользователем представление использовать.|  
  
## <a name="editor-factory-flags"></a>Флаги фабрики редактора  
  
|Значение|Описание|  
|-----------|-----------------|  
|[CEF. CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Устаревший флаг побитовым сочетанием как первый параметр <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> метод.|  
|[CEF. CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Побитовым сочетанием как первый параметр <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, метод, это указывает фабрика редактора должна внести необходимые исправления.|  
|[CEF. CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Побитовым сочетанием как первый параметр <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> , этот флаг является взаимно исключающим для [CEF. CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015).|  
|[CEF. CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Побитовым сочетанием как первый параметр <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> метода, это означает, фабрики редактора должна создать редактор без отображения пользовательского интерфейса (UI).|  
  
## <a name="visual-studio-errors"></a>Ошибки Visual Studio  
  
|Значение|Описание|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Константа возвращена интерфейсами для асинхронного поведения при рассматриваемый объект в уже занят|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Ошибка HRESULT, относящиеся к Visual Studio для «несовместимые данные документа».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Ошибка HRESULT для Visual Studio и что указывает «Пакет не загружен».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Ошибка HRESULT для Visual Studio и что указывает, что «Проекта уже существует».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Ошибка HRESULT для Visual Studio и указывает «ошибка конфигурации проекта».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Ошибка HRESULT для Visual Studio и, означающая «Проект не загружен».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Указывает ошибку HRESULT, относящиеся к Visual Studio, а «Решение уже открыть».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Ошибка HRESULT для Visual Studio и указывает «Решение не открыть».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Возвращается интерфейсами построения, которые имеют параметры для указания массива из <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> интерфейс, но реализацию можно применять только метод на все выходы.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Метод возвращает это значение, если документ имеет формат, который не может быть открыт в редакторе.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Значение HRESULT, указывающее, что пользователь нажал кнопку возврата в мастере Visual Studio.|  
  
## <a name="visual-studio-constants"></a>Константы Visual Studio  
  
|Значение|Описание|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Ошибка HRESULT для Visual Studio и, означающая «Проект перенаправлен».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Константа, которая относится к Visual Studio для панели элементов «маркером».|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Константа, которая относится к Visual Studio для трансляции сообщения с уведомлением через <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> метод, который указывает на начало модальности.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Константа, которая относится к Visual Studio для трансляции сообщения с уведомлением через <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> метод, который указывает на окончание модальности.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Константа, которая относится к Visual Studio для трансляции сообщения с уведомлением через <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> метод, указывающий, что показатели командной строки были изменены.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Константа, которая относится к Visual Studio, указывающая, что файл cookie не задан.|  
|[VSITEMID. Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Идентификатор элемента Visual Studio, представляющий отсутствие элемента проекта. Это значение используется в том случае, если нет текущего выделенного фрагмента.|
|[VSITEMID. Корневой](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Идентификатор элемента Visual Studio, который представляет корень иерархии проекта и используется для указания на всю иерархию, в отличие от одного элемента.|
|[VSITEMID. Выбор](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Идентификатор элемента Visual Studio, представляющий текущий выбранный элемент или элементы, которые могут включать корень иерархии.| 
  
## <a name="ivsselectionevents"></a>IVsSelectionEvents  
 Описывает, какие компоненты интегрированной среды разработки только что был выбран, в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> вызове, к примеру.  
  
|Константа|Значение|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1| 
  
## <a name="vsselelemid"></a>VSSELELEMID  
 Константы, используемые для указания нового состояния выделения.  
  
|Константа|Значение|  
|--------------|-----------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|  
  
## <a name="component-selector-dialog-constants"></a>Константы диалоговое окно выбора компонентов  
  
|Константа|Значение|  
|--------------|-----------|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|  
  
## <a name="see-also"></a>См. также  
 [Команды, определенные в интегрированной среде разработки, для расширения систем проектов](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
