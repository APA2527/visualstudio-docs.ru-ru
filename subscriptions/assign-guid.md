---
title: Назначение уникальных идентификаторов подписчикам Visual Studio | Документация Майкрософт
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.date: 10/22/2020
ms.topic: conceptual
description: Узнайте о том, как администраторы могут назначать уникальные идентификаторы (GUID) подписок подписчикам.
ms.openlocfilehash: 1097743d1640fbadba550f3c2ee6908ac694436d
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467483"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Посетите портал администрирования подписок Visual Studio, чтобы управлять подписками

Администраторы теперь могут использовать портал администрирования подписок Visual Studio для назначения подписок отдельным подписчикам.  Это может быть полезно в ситуациях, когда в компании есть временный персонал или поставщики, которым требуется доступ к подписке ненадолго.  Администраторы могут назначить подписку, которая уже была частично использована, а новые подписки будут использоваться для постоянных пользователей.  

Просмотрите видео или прочтите статью, чтобы узнать, как назначать пользователям определенные идентификаторы GUID подписок. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Назначение пользователям конкретных уникальных идентификаторов GUID подписки

Процесс назначения определенных подписок отдельным пользователям предполагает использование двух существующих процессов администрирования для назначения отдельным пользователям конкретных глобальных уникальных идентификаторов подписки (GUID).  Процесс из трех шагов включает в себя экспорт списка текущих подписок и назначений, использование этого списка для поиска конкретных идентификаторов GUID, которые необходимо назначить, а затем использование процесса массового добавления для отправки новых назначений.

### <a name="export-your-subscriptions-information"></a>Экспорт информации о ваших подписках

Чтобы выполнить экспорт:
1. Войдите на [портал администрирования](https://manage.visualstudio.com).
2. Выберите вкладку **Экспорт** , и файл загрузится на локальный компьютер. Имя файла будет содержать имя соглашения с подпиской вашего пользователя и датой экспорта.
> [!div class="mx-imgBorder"]
> ![Экспорт подписчиков](_img/exporting-subscriptions/exporting-subscriptions.png "Щелкните «Экспорт» , чтобы сохранить список назначенных подписок с данными о подписчике.")

### <a name="identify-the-guids-you-want-to-assign"></a>Укажите идентификаторы GUID, которые вы хотите назначить

Если вы ранее использовали инструмент экспорта, вы заметите, что в созданную электронную таблицу добавлены новые поля.  Они помогут определить состояние каждой подписки, а также указать, какие из них будут назначены пользователям.  

- **Состояние подписки** : В этом поле будет указано значение "назначена" или "не назначена".  Если подписка в состоянии "назначена", она также будет содержать связанные с ней сведения о пользователе, такие как имя, адрес электронной почты и т. д. 
- **Состояние использования** : В поле "состояние использования" будет указано "новая", что значит, что она никогда не была назначена пользователю, или "используется", что означает, что подписка уже была назначена пользователю.  

Можно использовать значения в этих полях вместе с другими сведениями в электронной таблице, чтобы определить, какие подписки необходимо назначить отдельным пользователям. Можно применить фильтр в Excel, чтобы сузить список по состоянию, уровню подписки, дате окончания срока действия и т. д. 

### <a name="upload-your-new-assignments"></a>Загрузка новых назначений

Последний шаг — скачать шаблон **Масового добавления** , заполнить необходимые сведения для подписок, которые нужно назначить, и отправить шаблон.  Полное описание этого процесса см. в статье [Добавление нескольких пользователей](assign-license-bulk.md).  

> [!IMPORTANT]
> Чтобы обеспечить успешную загрузку, убедитесь в том, что:
> - Используется шаблон, который был привязан в диалоговом окне при выборе элемента **Массовое добавление** .  Не используйте локальную копию шаблона, так как она может содержать не все обязательные поля.  Использование старой версии шаблона приведет к сбою при отправке. 
> - Все поля, отображаемые как **обязательные** в шаблоне, заполнены.
> - В столбце **Сообщение об ошибке** не указаны ошибки.
> - Каждый идентификатор GUID используется в шаблоне только один раз. 
> - Уровень подписки в шаблоне соответствует подписке GUID в экспортированном списке. 
> - Идентификатор GUID еще не назначен другому пользователю в экспортированном списке. 

## <a name="frequently-asked-questions"></a>Вопросы и ответы
### <a name="q-how-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>Вопрос: Как изменить подписку, назначенную отдельному пользователю?
Ответ. Если вы хотите изменить назначенный пользователю идентификатор GUID, сначала необходимо удалить подписку для этого пользователя.  Дополнительные сведения см. в нашей статье [Удаление подписки](delete-license.md).  После удаления подписки для этого пользователя используйте описанный выше процесс, чтобы экспортировать список и отправить новые сведения о подписке.  

## <a name="see-also"></a>См. также
- [Документация по Visual Studio](/visualstudio/)
- [Документация по Azure DevOps](/azure/devops/)
- [Документация по Azure](/azure/)
- [Документация по Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Следующие шаги
Теперь, когда вы назначили подписки пользователям, узнайте, как выполнять другие задачи администрирования.
- [Назначение отдельных подписок](assign-license.md)
- [Назначение нескольких подписок](assign-license-bulk.md)
- [Изменение подписок](edit-license.md)
- [Удаление подписок](delete-license.md)
- [Определение максимального использования](maximum-usage.md)


