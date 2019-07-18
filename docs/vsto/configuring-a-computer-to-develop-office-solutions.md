---
title: Настройка компьютера для разработки решений Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e559ddfec8570077a78fe980632366b4a57605de
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62930953"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Настройка компьютера для разработки решений Office

Чтобы создать надстройки VSTO и настройки для Microsoft Office, установите поддерживаемую версию Visual Studio, платформы .NET Framework и Microsoft Office.

|Программное обеспечение|Поддерживаемые версии|
|--------------|------------------------|
|Visual Studio 2017| Любой выпуск с **разработка для Office и SharePoint** рабочей нагрузки.|
|.NET Framework|— .NET Framework 4 или более поздней версии.|
|Microsoft Office|<ul><li>Любой выпуск набора Office, включая Office профессиональный плюс для Office 365.</li><li>Любое из следующих автономных приложений.<br /><br /> <ul><li>Excel</li><li>InfoPath (только в Office 2013 и Office 2010)</li><li>Outlook - приложение</li><li>PowerPoint</li><li>Проект</li><li>Visio</li><li>Слово</li></ul></li></ul><br /> Visual Basic для приложений (VBA) должен быть установлен как часть Office. **Внимание!** Версии приложения Office 2010 типа "нажми и работай" не поддерживаются.|

Подробное описание шагов установки, см. в разделе [как: Настройка компьютера для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Если шаблоны проекта не отображаются или не работают в Visual Studio

Если вы установили поддерживаемую версию Visual Studio, .NET Framework и Microsoft Office, а шаблоны проекта Office не отображаются в Visual Studio **новый проект** диалоговое окно, или произошла ошибка при попытке использовать один, Проверьте следующее:

- Проверьте, установлены ли на компьютер инструменты разработчика Microsoft Office.

     Инструменты разработчика Office являются дополнительным компонентом Visual Studio, но они устанавливаются автоматически вместе с Visual Studio. Если во время установки Visual Studio вы указываете, какие функции нужно установить, обязательно выберите элемент **Инструменты разработчика Microsoft Office** .

     Чтобы убедиться в том, что эти средства установлены, запустите программу установки Visual Studio и выберите **изменить** кнопки. Установите флажок возле элемента **Инструменты разработчика Microsoft Office** и нажмите кнопку **Обновить** .

- Убедитесь, что вы не используете версию Office, которое было доставлено, нажмите кнопку для запуска. См. практическое руководство по [ Проверить, является ли Outlook в приложении нажмите кнопку для запуска на компьютере](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Убедитесь, что у вас только одна версия Microsoft Office.

Если вы возникнут проблемы, см. в разделе [Дополнительные сведения об ошибках в решениях Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>См. также
- [Начало работы &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Практическое руководство. Настройка компьютера для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Практическое руководство. Установка средств Visual Studio для распространяемого пакета среды выполнения Office](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Практическое руководство. Установка основных сборок взаимодействия Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Введите доступность функций по типам приложений и проектов](../vsto/features-available-by-office-application-and-project-type.md)