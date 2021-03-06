---
title: Поддержка потоков в Office
description: В объектной модели Microsoft Office поддерживается многопоточность. Объектная модель Office не является потокобезопасной, но может работать с несколькими потоками в решении Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6fd35551c5c40494c169fb569113e3530f633a6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940804"
---
# <a name="threading-support-in-office"></a>Поддержка потоков в Office
  В этой статье содержатся сведения о поддержке потоков в объектной модели Microsoft Office. Объектная модель Office не является потокобезопасной, но можно работать с несколькими потоками в решении Office. Приложения Office являются серверами модели COM. COM позволяет клиентам вызывать серверы COM в произвольных потоках. Для COM-серверов, которые не являются потокобезопасными, COM предоставляет механизм сериализации одновременных вызовов, чтобы только один логический поток выполнялся на сервере в любое время. Этот механизм известен как модель однопотокового подразделения (STA). Поскольку вызовы сериализуются, вызывающие объекты могут блокироваться на периоды времени, когда сервер занят или обрабатывает другие вызовы в фоновом потоке.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>Сведения, необходимые при использовании нескольких потоков
 Для работы с несколькими потоками необходимо обладать как минимум базовыми знаниями о следующих аспектах многопоточности:

- API Windows

- Многопотоковые концепции COM

- Параллелизм

- Синхронизация

- Маршалинг

  Общие сведения о многопоточности см. в разделе [управляемые потоки](/dotnet/standard/threading/).

  Office работает в главном STA. Понимание последствий этого позволяет понять, как использовать несколько потоков с Office.

## <a name="basic-multithreading-scenario"></a>Базовый сценарий многопоточности
 Код в решениях Office всегда выполняется в основном потоке пользовательского интерфейса. Может потребоваться сгладить производительность приложения, выполняя отдельную задачу в фоновом потоке. Задача состоит в том, чтобы выполнить две задачи сразу вместо одной задачи, которая должна приводить к более гладкому выполнению (основная причина использования нескольких потоков). Например, у вас может быть код события в основном потоке пользовательского интерфейса Excel, а в фоновом потоке можно запустить задачу, собирающую данные с сервера, и обновлять ячейки в пользовательском интерфейсе Excel с данными с сервера.

## <a name="background-threads-that-call-into-the-office-object-model"></a>Фоновые потоки, вызывающие объектную модель Office
 Когда фоновый поток выполняет вызов приложения Office, вызов автоматически маршалируется через границу STA. Однако нет никакой гарантии, что приложение Office может справиться с вызовом во время его выполнения фоновым потоком. Существует несколько возможностей.

1. Приложение Office должно передавать сообщения для вызова, чтобы иметь возможность ввести. Если выполняется большая обработка без выполнения этой операции, это может занять некоторое время.

2. Если другой логический поток уже находится в подразделении, новый поток не сможет ввести. Это часто происходит, когда логический поток входит в приложение Office, а затем выполняет повторный вызов в подразделение вызывающего объекта. Приложение заблокировано, ожидая вызова.

3. Excel может находиться в таком состоянии, что он не может немедленно обрабатывать входящий вызов. Например, в приложении Office может отображаться модальное диалоговое окно.

   Для возможностей 2 и 3 COM предоставляет интерфейс [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) . Если сервер реализует его, все вызовы проходят через метод [хандлеинкомингкалл](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) . Для возможности 2 вызовы автоматически отклоняются. В случае 3, сервер может отклонить вызов в зависимости от обстоятельств. Если вызов отклоняется, вызывающий объект должен решить, что делать. Как правило, вызывающий объект реализует [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter), в этом случае он будет уведомлен о отклонении методом [ретрирежектедкалл](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) .

   Однако в случае решений, созданных с помощью средств разработки Office в Visual Studio, COM-взаимодействие преобразует все отклоненные вызовы в <xref:System.Runtime.InteropServices.COMException> ("фильтр сообщений сообщил, что приложение занято"). При каждом вызове объектной модели в фоновом потоке необходимо подготовиться к обработке этого исключения. Как правило, это подразумевает повторную попытку в течение определенного промежутка времени и последующее отображение диалогового окна. Однако можно также создать фоновый поток как STA, а затем зарегистрировать фильтр сообщений для этого потока, чтобы обрабатывал этот случай.

## <a name="start-the-thread-correctly"></a>Правильно запустить поток
 При создании нового потока STA перед запуском потока задайте для состояния подразделения значение STA. В следующем примере кода показано, как это сделать.

 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]

 Дополнительные сведения см. в разделе рекомендации по [управляемому потоку](/dotnet/standard/threading/managed-threading-best-practices).

## <a name="modeless-forms"></a>Немодальные формы
 Немодальная форма позволяет выполнить некоторый тип взаимодействия с приложением во время отображения формы. Пользователь взаимодействует с формой, и форма взаимодействует с приложением без закрытия. Объектная модель Office поддерживает управляемые немодальные формы; Однако они не должны использоваться в фоновом потоке.

## <a name="see-also"></a>См. также раздел
- [Работа с потоками (C#)](/dotnet/csharp/programming-guide/concepts/threading/index)
- [Работа с потоками (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [Использование потоков и потоков](/dotnet/standard/threading/using-threads-and-threading)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
