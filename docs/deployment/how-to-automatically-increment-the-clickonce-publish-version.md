---
title: Практическое руководство. Автоматически ClickOnce увеличение номера версии публикации | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cce9dfe48e34d642b115c8391de73c0350ce515b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928502"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Практическое руководство. автоматическое увеличение номера версии публикации ClickOnce

При публикации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения, изменив `Publish Version` свойство заставляет приложение публикуется как обновление. По умолчанию Visual Studio автоматически увеличивает `Revision` число `Publish Version` при каждой публикации приложения.

Это поведение можно отключить на **публикации** странице **конструктор проектов**.

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Сброс параметров](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Автоматическое отключение увеличения номера версии публикации

1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.

2. Перейдите на вкладку **Публикация**.

3. В **версия публикации** снимите **автоматически увеличивать номер редакции при каждой редакции** "флажок".

## <a name="see-also"></a>См. также

- [Практическое руководство. Установка версии публикации приложения ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)