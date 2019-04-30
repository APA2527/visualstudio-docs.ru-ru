---
title: Практическое руководство. Отключение активации ClickOnce-приложений по URL-адрес с помощью конструктора | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4da1ba726253891ef7df2ccfde8a667ac11ad8d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928584"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Практическое руководство. отключение активации приложений ClickOnce по URL-адресу при помощи конструктора
Как правило [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения будет запускаться автоматически сразу после его установки на веб-сервере. По соображениям безопасности можно отключить это поведение и сообщить пользователям, чтобы запустить приложение из **запустить** меню вместо этого. Следующая процедура описывает процесс отключения активации через URL.

 Такой подход можно использовать только для приложений [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], установленных на компьютере пользователя с веб-сервера. Он не может использоваться для интерактивных приложений, которые могут быть запущены только с помощью URL-адрес. Дополнительные сведения о различиях между только в Интернете и установленными приложениями см. в разделе [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

 В этой процедуре используется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Кроме того, эту задачу можно решить с помощью [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Дополнительные сведения см. в разделе [Как отключить активацию по URL-адресу приложений ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## <a name="procedure"></a>Процедура

#### <a name="to-disable-url-activation-for-your-application"></a>Отключение активации приложения с помощью URL

1. Щелкните правой кнопкой мыши имя проекта в **обозревателе решений**и нажмите кнопку **свойства**.

2. На **свойства** щелкните **публикации** вкладки.

3. Щелкните **Параметры**.

4. Нажмите кнопку **манифесты**.

5. Выберите флажок **Блокировать активацию с помощью URL-адреса приложения с**.

6. Развертывание приложения.

## <a name="see-also"></a>См. также
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)