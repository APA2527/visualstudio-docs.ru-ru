---
title: Выберите диалоговое окно «операции» (для прежних версий) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b42ecd7ad38144786ff12d5cad20c9e8a1437646
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417554"
---
# <a name="choose-operation-dialog-box-legacy"></a>Диалоговое окно «Выбор операции» (для прежних версий)
Здесь описывается, как использовать **выбрать операцию** диалогового окна в прежних версий [!INCLUDE[wfd1](../includes/wfd1-md.md)]. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 **Выбрать операцию** диалоговое окно используется для выбора операции, связанной с <xref:System.Workflow.Activities.ReceiveActivity> действия или <xref:System.Workflow.Activities.SendActivity> действия. Дополнительные сведения об использовании это диалоговое окно с этими действиями см. в разделе [как: Реализация операции контракта WCF (для прежних версий)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) и [как: Вызов операции контракта WCF (для прежних версий)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).  
  
 В следующей таблице описаны элементы пользовательского интерфейса (UI) **выбрать операцию** диалоговое окно.  
  
|Элемент пользовательского интерфейса|Описание|  
|----------------|-----------------|  
|**Добавление контракта**|Создает новый контракт. В этом контракте можно задать новые операции. (Применяется только с объектом класса <xref:System.Workflow.Activities.ReceiveActivity>.)|  
|**Добавить операцию**|Добавляет новые операции в новый контракт, созданный в **выбрать операцию** диалоговое окно. **Примечание.**  Можно добавить новые операции только в контракты, которые созданы посредством **выбрать операцию** диалоговое окно. <br /><br /> (Применяется только с объектом класса <xref:System.Workflow.Activities.ReceiveActivity>.)|  
|**Импорт...**|Импорт ранее определенного контракта, позволяет выбрать операцию из этого контракта.|  
|**Имя операции**|Имя выбранной в настоящее время операции. Это текстовое поле доступно для изменения только в том случае, если вы создали операцию через **выбрать операцию** диалоговое окно.|  
|**Параметры**|Вкладка, содержащая определения параметров выбранной в настоящее время операции. **Примечание.**  Определения параметров можно изменить только в том случае, если вы создали операцию через **выбрать операцию** диалоговое окно.|  
|**Свойства**|Вкладка, содержащая параметры <xref:System.Net.Security.ProtectionLevel> для сообщений, отправляемых между клиентом и службой. **Примечание.**  Эта вкладка активна только в том случае, если вы создали операцию через **выбрать операцию** диалоговое окно.|  
|**Разрешения**|Вкладка содержит свойства пользователей <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> и <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A>, которые разрешается вызывать этой операции. Например, если только пользователи из группы администраторов разрешено вызывать эту операцию, то необходимо написать «Администраторы» **роли** текстовое поле.<br /><br /> Эта вкладка активна для обеих операций, созданных с помощью **ChooseOperation** диалоговое окно и операций, которые были импортированы через **импорта** кнопки.|  
  
> [!NOTE]
> **Выбрать операцию** диалоговое окно показывает только контракты или операции, которые используются другими <xref:System.Workflow.Activities.SendActivity> действий рабочего процесса. Аналогичным образом **выбрать операцию** диалоговое окно для <xref:System.Workflow.Activities.ReceiveActivity> действий показывает только контракты или операции, которые используются другими **ReceiveActivity** действий рабочего процесса.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Реализация операции контракта WCF (для прежних версий)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Практическое руководство. Вызов операции контракта WCF (для прежних версий)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Справка по интерфейсу пользователя конструктора прежних версий для Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)