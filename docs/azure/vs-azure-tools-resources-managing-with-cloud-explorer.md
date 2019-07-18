---
title: Управление ресурсами Azure с помощью Cloud Explorer | Документация Майкрософт
description: Узнайте, как использовать Cloud Explorer для просмотра ресурсов Azure и управления ими в Visual Studio.
author: ghogen
manager: jillfra
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: 2abfb87ff4a97201246f9a9c284871db5e5f0068
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62572721"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Управление ресурсами, связанными с учетными записями Azure, с помощью Visual Studio Cloud Explorer

Cloud Explorer позволяет просматривать ресурсы и группы ресурсов Azure, проверять их свойства и выполнять основные диагностические действия разработчика в среде Visual Studio.

Приложение Cloud Explorer, как и [портал Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040), основано на стеке Azure Resource Manager. Благодаря этому Cloud Explorer распознает ресурсы (например, группы ресурсов Azure) и службы Azure (например, Logic Apps и API-приложения), а также поддерживает [управление доступом на основе ролей](/azure/role-based-access-control/role-assignments-portal) (RBAC).

## <a name="prerequisites"></a>Предварительные требования

* Visual Studio 2017 или последующей версии (см. страницу [скачивания Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)) с выбранной **рабочей нагрузкой Azure**. Вы также можете использовать предыдущие версии Visual Studio с [Пакетом Microsoft Azure SDK для .NET 2.9](https://www.microsoft.com/download/details.aspx?id=51657).
* Учетная запись Azure. Если у вас ее нет, [зарегистрируйтесь для работы с бесплатной пробной версией](http://go.microsoft.com/fwlink/?LinkId=623901) или [активируйте преимущества для подписчиков Visual Studio](http://go.microsoft.com/fwlink/?LinkId=623901).

> [!NOTE]
> Чтобы открыть Cloud Explorer, нажмите клавиши **CTRL**+**Q**, чтобы активировать поле поиска, и введите **Cloud Explorer**.

## <a name="add-an-azure-account-to-cloud-explorer"></a>Добавление учетной записи Azure в Cloud Explorer

Чтобы просмотреть ресурсы, связанные с учетной записью Azure, сначала необходимо добавить учетную запись в **Cloud Explorer**.

1. В **Cloud Explorer** нажмите кнопку **Управление учетными записями**.

   ![Значок параметров учетной записи Azure в Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Выберите **Управление учетными записями**.

   ![Ссылка для добавления учетной записи в Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Войдите в учетную запись Azure, ресурсы которой хотите просмотреть.

1. Войдя в учетную запись Azure, вы увидите подписки, связанные с этой учетной записью. Установите флажки для тех подписок учетной записи, которые вы хотите просмотреть, а затем выберите **Применить**.

   ![Cloud Explorer: выбор подписок Azure для отображения](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Когда вы завершите выбор нужных подписок, в Cloud Explorer отобразятся все ресурсы этих подписок.

   ![Список ресурсов для учетной записи Azure в Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Удаление учетной записи Azure в Cloud Explorer

1. В **Cloud Explorer** выберите **Управление учетными записями**.

   ![Значок параметров учетной записи Azure в Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Рядом с учетной записью, которую вы хотите удалить, выберите **Управление учетными записями**.

   ![Значок параметров учетной записи Azure в Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Щелкните **Удалить**, чтобы удалить учетную запись.

    ![Диалоговое окно "Управление учетными записями" в Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Просмотр типов или групп ресурсов

Для просмотра ресурсов Azure вы можете выбрать представление **Типы ресурсов** или **Группы ресурсов**.

1. В **Cloud Explorer** выберите раскрывающийся список представления ресурсов.

   ![Раскрывающийся список Cloud Explorer, который позволяет выбрать нужное представление ресурсов](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. В контекстном меню выберите нужное представление:

   * Представление **Типы ресурсов**, которое часто используется на [портале Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040), отображает ресурсы Azure с упорядочением по типам (веб-приложения, виртуальные машины, учетные записи хранения и т. п.).
   * Представление **Группы ресурсов** упорядочивает ресурсы Azure по группам ресурсов Azure, с которыми они связаны. Группа ресурсов представляет собой набор ресурсов Azure, обычно используемых в конкретном приложении. Дополнительные сведения о группах ресурсов Azure см. в статье [Общие сведения о диспетчере ресурсов Azure](/azure/azure-resource-manager/resource-group-overview).

   На следующем рисунке для сравнения изображены оба представления ресурсов:

   ![Сравнение представлений ресурсов в Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Просмотр и поиск ресурсов в Cloud Explorer

В Cloud Explorer вы можете перейти к ресурсу Azure, чтобы просмотреть связанные сведения. Для этого разверните тип ресурса или группу, к которой он относится, и выберите в списке нужный ресурс. Когда вы выберете ресурс, информация о нем появится на двух вкладках в нижней части Cloud Explorer — **Действия** и **Свойства**.

* На вкладке **Действия** отображаются действия, которые можно выполнить в Cloud Explorer для выбранного ресурса. Эти же варианты действий можно получить в контекстном меню ресурса, которое открывается по щелчку на ресурсе правой кнопкой мыши.

* На вкладке **Свойства** отображаются свойства ресурса, например его тип, язык и региональные стандарты и группа ресурсов, с которой связан ресурс.

На следующем рисунке для сравнения представлены сведения, отображаемые на каждой вкладке для службы приложений:

  ![Снимок экрана Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Для каждого ресурса доступно действие **Открыть на портале**. При выборе этого действия приложение Cloud Explorer отобразит выбранный ресурс на [портале Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040). Функция **Открыть на портале** особенно удобна для перехода к ресурсам с глубоким уровнем вложенности.

Также для конкретных ресурсов Azure могут отображаться другие действия и свойства. Например, для веб-приложений и приложений логики, помимо стандартного действия **Открыть на портале**, также доступны действия **Открыть в браузере** и **Подключить отладчик**. При выборе больших двоичных объектов учетной записи хранения, очередей или таблиц отображаются действия их открытия в редакторах. У приложений Azure есть свойства **URL-адрес** и **Состояние**, а для ресурсов хранилища в свойствах указаны ключ доступа и строка подключения.

## <a name="find-resources-in-cloud-explorer"></a>Поиск ресурсов в Cloud Explorer

Чтобы найти в подписках учетной записи Azure ресурс с известным именем, введите это имя в поле **Поиск** в Cloud Explorer.

  ![Поиск ресурсов в обозревателе облака](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

По мере ввода символов в поле **Поиск** в дереве ресурсов остаются только те ресурсы, имена которых соответствуют этим символам.
