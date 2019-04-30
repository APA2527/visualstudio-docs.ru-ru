---
title: Конструктор рабочих процессов - конструктор действия Receive
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bcab59a631b1dbf9c85c7bff2454a42e97accff8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969336"
---
# <a name="receive-activity-designer"></a>Конструктор действия Receive

**Receive** конструктора действий используется для создания и настройки <xref:System.ServiceModel.Activities.Receive> действия. Действие <xref:System.ServiceModel.Activities.Receive> получает сообщение - либо встроенное, например <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> или <xref:System.Xml.Linq.XElement>, либо определяемое контрактом данных приложения, контрактом сообщений или классом XML, поддерживающим сериализацию.

## <a name="the-receive-activity"></a>Действие Receive

Действие <xref:System.ServiceModel.Activities.Receive> может получать один или несколько элементов в зависимости от используемого типа приема содержимого. Действие <xref:System.ServiceModel.Activities.SendReply> может быть привязано к действию <xref:System.ServiceModel.Activities.Receive>, которое получает сообщение в процессе обмена сообщениями по шаблону «запрос-ответ» на стороне службы.

### <a name="using-the-receive-activity-designer"></a>Использование конструктора действия Receive

Доступ **Receive** конструктора действий в **Messaging** категории **элементов**. **Receive** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, везде, где обычно размещаются действия. При этом создается действие <xref:System.ServiceModel.Activities.Receive> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Receive. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **Receive** конструктора действий или в **DisplayName** поле таблицы свойств.

Для создания <xref:System.ServiceModel.Activities.SendReply> действия и привязать его к выбранному <xref:System.ServiceModel.Activities.Receive> действия, щелкните правой кнопкой мыши **Receive** конструктора, щелкните действие **создать SendReply** элемента в контекстном меню и **SendReplyToReceive** появится ниже конструктора **Receive** конструктора. Действие <xref:System.ServiceModel.Activities.SendReply> отправляет ответное сообщение в процессе обмена сообщениями по шаблону «запрос-ответ» на стороне службы. Его можно настроить с помощью **SendReplyToReceive** конструктора.

Кроме того **ReceiveAndSendReply** конструктора шаблонов в **Messaging** категории **элементов** можно использовать для создания пары предварительно настроенных <xref:System.ServiceModel.Activities.Receive>и <xref:System.ServiceModel.Activities.SendReply> действия. Дополнительные сведения об использовании **ReceiveAndSendReply** и **SendReplyToReceive** шаблон, см. в разделе [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) раздела.

### <a name="the-receive-activity-properties"></a>Свойства действия Receive

В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.Receive> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в рабочей области конструктора рабочих процессов. Свойство <xref:System.ServiceModel.Activities.Receive.OperationName%2A> является единственным обязательным свойством.

| Имя свойства | Обязательно | Использование |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Указывает понятное имя действия <xref:System.ServiceModel.Activities.Receive>. Значение по умолчанию - Receive.<br /><br /> Несмотря на то, что использовать значение, отличное от значения по умолчанию, для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не требуется, его все же рекомендуется использовать. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | True | Указывает имя операции службы, реализуемой этим действием <xref:System.ServiceModel.Activities.Receive>. Это свойство используется для создания значения по умолчанию для **действие** свойство Если **действие** свойство не задано явно. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | False | Задает имя контракта службы. Данное свойство используется для группирования операций служб в отдельные контракты служб. Все действия <xref:System.ServiceModel.Activities.Receive>, которые имеют одинаковое имя контракта <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>, группируются по этому контракту службы (тип порта WSDL). Значение по умолчанию — полное имя CLR действия верхнего (корневого) уровня. |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | False | Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Это свойство можно изменить, нажав кнопку с многоточием рядом с **содержимого** в таблице свойств или нажав **определение...**  рядом с **содержимого** метки на **Receive** рабочей области конструктора действий. Как отобразить **определение содержимого** диалоговое окно. Дополнительные сведения о том, как использовать это окно, см. в разделе [содержимого диалогового окна определения](../workflow-designer/content-definition-dialog-box.md) раздела. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | False | Указывает корреляции между действиями <xref:System.ServiceModel.Activities.Receive> в операциях службы рабочего процесса с объектом <xref:System.ServiceModel.MessageQuerySet>. Нажмите кнопку с многоточием рядом с полем <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> свойства в сетке свойств, чтобы открыть **корреляция по определению** диалоговое окно. Дополнительные сведения об использовании этого диалогового окна см. в разделе [содержимого диалогового окна определения](../workflow-designer/content-definition-dialog-box.md) раздела. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | False | Задает метод <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для перенаправления сообщения в соответствующий экземпляр рабочего процесса.<br /><br /> Нажмите кнопку с многоточием рядом с полем <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> свойства в сетке свойств, чтобы открыть **редактор выражений** диалоговое окно. Дополнительные сведения об использовании этого диалогового окна см. в разделе [как: Использовать редактор выражений](../workflow-designer/how-to-use-the-expression-editor.md) раздела. |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | False | Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку с многоточием рядом с полем <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> свойства в сетке свойств, чтобы открыть **Добавление инициализаторов корреляции** диалоговое окно. Дополнительные сведения об использовании это окно, см. в разделе [CorrelationInitializers диалоговое окно Добавление](../workflow-designer/add-correlationinitializers-dialog-box.md) раздела. |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | False | Указывает значение, которое определяет, может ли быть создан новый экземпляр рабочего процесса для обработки сообщения в случае, если сообщение не соответствует существующему экземпляру рабочего процесса. Если присвоено значение **true**, будет создан новый экземпляр рабочего процесса для обработки сообщения, если сообщение не соответствует существующему экземпляру рабочего процесса. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | False | Указывает коллекцию известных типов для операции службы, реализуемой этим действием <xref:System.ServiceModel.Activities.Receive>. Это свойство должно использоваться вместе со свойством <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>, установленным в значение <xref:System.Runtime.Serialization.DataContractSerializer>. Не учитывается, если используется <xref:System.Xml.Serialization.XmlSerializer>.<br /><br /> Выберите кнопку с многоточием рядом с **KnownTypes** в таблице свойств для отображения **редактор коллекции типов** диалоговое окно, с помощью которого можно добавить необходимые типы. Дополнительные сведения об использовании это окно, см. в разделе [диалоговое окно редактора коллекции типа](../workflow-designer/type-collection-editor-dialog-box.md) раздела. |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | False | Задает <xref:System.Net.Security.ProtectionLevel> для сообщения.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> означает только проверку подлинности.<br />2. <xref:System.Net.Security.ProtectionLevel> означает необходимость подписи данных для обеспечения целостности передаваемых данных.<br />3. <xref:System.Net.Security.ProtectionLevel> означает необходимость шифрования и подписи данных для обеспечения конфиденциальности и целостности передаваемых данных. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | False | Указывает тип используемого сериализатора для операции службы, реализуемой действием <xref:System.ServiceModel.Activities.Receive>. Значение по умолчанию равно <xref:System.Runtime.Serialization.DataContractSerializer>, при котором выполняется сериализация и десериализация экземпляра типа в XML-поток или документ, который использует переданный контракт данных. <xref:System.Xml.Serialization.XmlSerializer> также может быть использован в том случае, если необходим больший контроль над XML. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | False | Указывает заголовок действия сообщения. Если оно не задано явно, его значение по умолчанию: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>См. также

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
