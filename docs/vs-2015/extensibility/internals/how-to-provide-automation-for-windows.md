---
title: Практическое руководство. Автоматизация для Windows | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ea7b79df4e7f3748ec2bc7f5e57c6ecb7dfca5b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191843"
---
# <a name="how-to-provide-automation-for-windows"></a>Практическое руководство. Автоматизация для окон
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Вы можете предоставить автоматизация для окон документов и средств. Предоставление автоматизации рекомендуется всякий раз, когда вы хотите сделать объекты автоматизации доступными в окне и среде уже не предоставить объект готовые службы автоматизации, как в случае со списком задач.  
  
## <a name="automation-for-tool-windows"></a>Модель автоматизации для инструментов Windows  
 Среды обеспечивает автоматизацию в окне инструментов, возвращая стандартный <xref:EnvDTE.Window> объекта, как описано в следующей процедуре:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Для обеспечения автоматизации окна инструментов  
  
1. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод через среду со <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> как `VSFPROPID` для получения `Window` объекта.  
  
2. Когда вызывающий объект запрашивает объект автоматизации определенного VSPackage для вашего окна инструментов через <xref:EnvDTE.Window.Object%2A>, среда вызывает метод `QueryInterface` для `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, или `IDispatch` интерфейсов. Оба `IExtensibleObject` и `IVsExtensibleObject` предоставляют <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> метод.  
  
3. Когда среде затем вызывает метод `GetAutomationObject` метод `NULL`, ответ, передав резервного объекта определенного VSPackage.  
  
4. Если вызов `QueryInterface` для `IExtensibleObject` и `IVsExtensibleObject` завершается ошибкой, то среда вызывает `QueryInterface` для `IDispatch`.  
  
## <a name="automation-for-document-windows"></a>Модель автоматизации для документа Windows  
 Стандартный <xref:EnvDTE.Document> объекта также доступна из среды, несмотря на то, что редактор может иметь собственную реализацию `T:EnvDTE.Document` объекта путем реализации `IExtensibleObject` интерфейс и реагирование на них `GetAutomationObject`.  
  
 Кроме того, редактор можно предоставить объект автоматизации определенного VSPackage, полученные через <xref:EnvDTE.Document.Object%2A> метод путем реализации `IVsExtensibleObject` или `IExtensibleObject` интерфейсов. [Примеры VSSDK](../../misc/vssdk-samples.md) участвует объект автоматизации конкретного документа RTF.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
