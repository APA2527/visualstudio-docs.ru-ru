---
title: Вход в подписки Visual Studio может быть неудачным при использовании псевдонимов | Документы Майкрософт
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/02/2018
ms.topic: conceptual
description: Вход может завершиться ошибкой, если используются дополнительные имена (псевдонимы)
searchscope: VS Subscription
ms.openlocfilehash: ac3f9df365e0b7924b615c2ae8cbb70d93d04948
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946186"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Вход в подписки Visual Studio может быть неудачным при использовании псевдонимов

В зависимости от типа учетной записи при входе в систему [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) могут неправильно отображаться доступные подписки. Одна из причин такой проблемы — использование дополнительных имен вместо идентификатора входа, которому назначена подписка. Это называется "применение псевдонимов".

## <a name="what-is-aliasing"></a>Что такое применение псевдонимов?

Термин "применение псевдонимов" относится к ситуации, при которой пользователи могут использовать разные идентификаторы для входа в Windows (или в Active Directory) и доступа к электронной почте.

Например, работа компании может быть организована так, что для входа в основной каталог используется учетная запись Microsoft Online, например JohnD@contoso.com, а для работы с электронной почтой пользователи вводят другие имена (псевдонимы), например John.Doe@contoso.com. Для многих пользователей, которые управляют подпиской при помощи Volume Licensing Service Center (VLSC), это может привести к неудачным попыткам входа в систему, так как предоставленный адрес электронной почты (John.Doe@contoso.com) не совпадает с адресом для каталога (JohnD@contoso.com), необходимым для правильной аутентификации по методу "Рабочая или учебная учетная запись".

## <a name="as-an-administrator-what-options-do-i-have"></a>Какие в этой ситуации есть варианты у администратора?

У администратора такой системы есть два способа обеспечить подписчикам успешный вход в систему [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
- Первый вариант — применять в качестве адреса назначения в Volume Licensing Service Center (VLSC) исключительно учетную запись каталога. Рекомендуем использовать именно этот метод. Подробности вы найдете в разделе этой статьи [Назначение подписчиков учетной записи каталога](#assigning-subscribers-to-a-directory-account).
- Второй вариант (менее безопасный) — предоставить подписчикам право связать рабочий или учебный адрес электронной почты с личной учетной записью (учетной записью Майкрософт, MSA). Дополнительные сведения см. в разделе [Определение рабочей или учебной учетной записи как личной учетной записи](#defining-a-work-or-school-account-as-a-personal-account) этой статьи.

> [!NOTE]
> Когда компания выполнит миграцию на новый [портал управления](https://manage.visualstudio.com) подписками Visual Studio, вы сможете воспользоваться преимуществами нового интерфейса администрирования, который позволяет указать в профиле подписчика одновременно и адрес электронной почты, и адрес каталога. Подробнее о миграции см. [здесь](https://support.microsoft.com/help/4013930/visual-studio-subscriptions-administrator-migration-details).

## <a name="as-a-subscriber-what-options-do-i-have"></a>Какие в этой ситуации есть варианты у подписчика?

С точки зрения подписчика здесь важно правильно взаимодействовать с администратором, чтобы составить представление о системе удостоверений в вашей компании. Возможно, администратору потребуется обновить параметры вашей учетной записи на портале администрирования или вам нужно будет создать учетную запись Майкрософт на основе рабочего адреса электронной почты. Прежде чем создавать MSA, обсудите с администратором политику в отношении таких действий и возможные проблемы. Дополнительные сведения см. в разделе [Определение рабочей или учебной учетной записи как личной учетной записи](#defining-a-work-or-school-account-as-a-personal-account) этой статьи.

## <a name="assigning-subscribers-to-a-directory-account"></a>Назначение подписчиков учетной записи каталога

Диспетчер подписки в Volume Licensing Service Center (VLSC) обязательно должен использовать для новых подписчиков адрес каталога или обновить адреса электронной почты для существующих подписчиков. Важно отметить, что при использовании адреса каталога новые подписчики не смогут получать приветственные сообщения по электронной почте. Это значит, что администратору придется другим способом уведомлять их о назначении подписки. Выполнив описанные ниже шаги, вы можете применить [шаблон](#notifying-your-subscribers-with-directory-addresses) сообщения электронной почты, чтобы оповестить подписчиков и предоставить им информацию о процессе входа.

### <a name="adding-new-subscribers"></a>Добавление новых подписчиков

Выполните приведенные ниже инструкции, чтобы добавить нового подписчика на основе учетной записи каталога.

1. Откройте [Volume Licensing Service Center (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx) и выполните вход.
2. На странице администрирования Volume Licensing Service Center щелкните **Подписки** и выберите **Подписки Visual Studio**.

    > [!div class="mx-imgBorder"]
    > ![Меню "Подписки"](_img//vlsc/vlsc-subscriptions.png)

3. Выберите **номер соглашения**, связанный с нужной подпиской Visual Studio.

    > [!div class="mx-imgBorder"]
    > ![Выбор соглашения](_img/vlsc/vlsc-agreement.png)

4. Щелкните **Assign Subscription** (Назначить подписку).
5. Выберите нужный **уровень подписки**.
6. Убедитесь, что есть доступные для назначения подписки, и нажмите кнопку **Далее**.
7. Введите сведения о подписчике и адрес каталога в поле адреса электронной почты, затем нажмите кнопку **Далее**.
8. Проверьте сведения о подписчике и нажмите кнопку **Готово**.
9. Известите подписчика о том, что для него подготовлена подписка, при помощи предложенного ниже [шаблона письма](#notifying-your-subscribers-with-directory-addresses).

### <a name="updating-an-existing-subscriber"></a>Обновление существующего подписчика

Выполните описанные ниже действия, чтобы сохранить учетную запись каталога для существующего подписчика.

1. Откройте [Volume Licensing Service Center (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx) и выполните вход.
2. На сайте администрирования Volume Licensing Service Center щелкните **Подписки** и выберите **Подписки Visual Studio**.
3. Выберите **номер соглашения**, связанный с нужной подпиской Visual Studio.
4. Щелкните **стрелку вниз** на панели поиска.
5. Выполните поиск подписчика при помощи поля "Адрес электронной почты".
6. В списке результатов щелкните **фамилию** подписчика.
7. Нажмите кнопку **Правка**.
8. Введите нужный адрес каталога в поле "Адрес электронной почты" и нажмите кнопку **Сохранить**.
9. Известите подписчика о том, что для него подготовлена подписка, при помощи предложенного ниже шаблона письма.

### <a name="notifying-your-subscribers-with-directory-addresses"></a>Уведомление подписчика с указанием адреса каталога

Так как приветственное сообщение не будет доставлено этому подписчику по электронной почте, скопируйте следующий текст, вставьте его в клиент электронной почты и отправьте подписчику. Замените все слова вида %ИНФОРМАЦИЯ% соответствующими сведениями о конкретном подписчике.

```
----------- Copy Below (Ctrl+C) -----------

Hello %SUBSCRIBER NAME%

You have been assigned a Visual Studio subscription. Please visit https://my.visualstudio.com, and log in with your %DIRECTORY ADDRESS% address to activate and access your subscription.

If you’re having trouble, please contact the support team (https://visualstudio.microsoft.com/subscriptions/support/).

At the bottom of the page, select the following:
   - Accounts, Subscriptions, and Billing Support
   - From Issue, choose Subscription sign in support
   - Choose the appropriate Country
   - Select the desired Assisted Support option

----------- End Copy -----------
```

## <a name="defining-a-work-or-school-account-as-a-personal-account"></a>Определение рабочей или учебной учетной записи как личной учетной записи

Чтобы добавить нового пользователя или обновить адрес электронной почты в Volume Licensing Service Center (VLSC), выполните инструкции из раздела [Назначение подписчиков учетной записи каталога](#assigning-subscribers-to-a-directory-account).  Если каталог не распознает адрес электронной почты, нужно создать новую учетную запись, чтобы определить адрес электронной почты как личную учетную запись.  В качестве временного решения команда подписок Visual Studio обеспечила исключение из описанной ниже политики идентификации, но мы работаем над тем, чтобы отменить эту политику.

> [!WARNING]
> Корпорация Майкрософт не рекомендует объединять рабочие или учебные идентификаторы с личными.  Такое объединение приводит к потере контроля за учетными записями, и в определенных случаях сотрудники сохраняют доступ к некоторым продуктам и (или) службам даже после прекращения работы в компании.  Дополнительные сведения см. в [этой записи блога](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/15/cleaning-up-the-azure-ad-and-microsoft-account-overlap/) группы Microsoft Identity.

### <a name="defining-an-email-address-as-a-personal-account"></a>Определение адреса электронной почты как личной учетной записи

После того как подписка будет назначена определенному подписчику, ему по электронной почте направляется письмо с предложением перейти к странице [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs), на которой можно использовать преимущества этой подписки.  При попытке входа в систему подписок Visual Studio он получит сообщение об ошибке, так как учетная запись не распознана.  Поэтому перед входом на портал [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) вашему подписчику нужно выполнить приведенные ниже инструкции.  При необходимости примените [этот шаблон](#notifying-your-subscribers-using-personal-accounts) для извещения подписчика о назначении подписки.

1. Откройте страницу https://my.visualstudio.com и щелкните **Создать новую учетную запись Майкрософт**.

2. Заполните поля данных:
   - введите адрес электронной почты, по которому отправлено приветственное сообщение, в поле Someone@example.com;
   - создайте пароль;
   - выберите параметры рекламных акций;
   - Нажмите кнопку **Далее**.

3. Выполните процессы проверки и нажмите кнопку **Далее**.

4. Возможно, новому пользователю потребуется заполнить профиль Visual Studio.

5. Теперь для него будет доступна подписка и ее преимущества.

### <a name="notifying-your-subscribers-using-personal-accounts"></a>Уведомление подписчиков, использующих личные учетные записи

В описанном выше сценарии подписчик успешно получат приветственное сообщение по электронной почте, но из-за применения псевдонимов он может столкнуться с проблемами при входе.  Приведенный ниже текст поможет вам известить подписчика о выполненных действиях и предоставить ему сведения о получении поддержки, если она ему потребуется.  Замените все слова вида %ИНФОРМАЦИЯ% соответствующими сведениями о конкретном подписчике.

```
----------- Copy Below (Ctrl+C) -----------

Hello %SUBSCRIBER NAME%

You have been assigned a Visual Studio subscription, and may have been directed to log into https://my.visualstudio.com based on your Welcome email.  While this is the correct website for consuming benefits, our organization requires you to take a few extra steps before you can access the site.  Please follow the below instructions to help you create a “Microsoft Account” that is tied to our corporate email address.  Once these steps are completed, you will use your email address to access the Subscription benefits.
1. Visit https://my.visualstudio.com

2. Click Create new Microsoft Account on the right hand side

3. Complete the Form:
   - Use your corporate email address in the someone@example.com box
   - Enter a password
   - Select your promotional preference
   - Click Next

4. Complete the account validation steps

5. If necessary, complete the Visual Studio profile

6. You should now see your benefits

Note:  When visiting https://my.visualstudio.com in the future, you may be prompted to select which account you’d like to use (e.g. “Work or School Account” or “Personal Account”).  After following the steps above, you will need to leverage the “Personal Account” option.

If you’re having trouble, please contact the support team (https://visualstudio.microsoft.com/subscriptions/support/).

At the bottom of the page, select the following:
   - Accounts, Subscriptions, and Billing Support
   - From Issue, choose Subscription sign in support
   - Choose the appropriate Country
   - Select the desired Assisted Support option

----------- End Copy -----------
```
