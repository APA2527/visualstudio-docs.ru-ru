---
title: Создание пакета расширения с помощью шаблона элемента пакета расширения | Документация Майкрософт
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: gregvanl
ms.author: gregvanl
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 7899a096bb2a56e93ea55a4ba0a17cde272bd615
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62950976"
---
# <a name="walkthrough-create-an-extension-pack"></a>Пошаговое руководство. Создание пакета расширения

Пакет расширения — это набор расширений, которые могут быть установлены вместе. Пакеты расширения позволяют легко поделиться избранные расширения с другими пользователями или объединить набор расширений для конкретного сценария.

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, Visual Studio SDK входит в состав дополнительным компонентом в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

Функция Extension Pack доступен, начиная с Visual Studio 15.8 предварительной версии 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Создание расширения с помощью шаблона элемента Extension Pack

Шаблон элемента Extension Pack создает пакет расширения с помощью набора расширений, которые могут быть установлены вместе.

1. В **новый проект** диалоговое окно, и выполните поиск «vsix» и выберите **проект VSIX**. Для **имя_проекта**, введите «Пакета расширения тестирования». Выберите **Создать**.

2. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить** > **новый элемент**. Перейдите в Visual C# **расширяемости** узел и выберите **пакет расширений**. Оставьте имя файла по умолчанию (ExtensionPack1.cs).

3. Добавляется файл ExtensionPack1.vsext, который содержит следующий код

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }
   ```

4. Vsixid расширения для включения в пакет расширений можно найти на [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Найдите нужное расширение и нажмите кнопку на **идентификатор копирования**. Вы можете обновить существующий **vsixId** выше файл или добавить другое расширение в список.

    ![Скопируйте VsixId из Marketplace](media/vsixid-marketplace.png)

5. Постройте проект и отправки расширения в Marketplace. См. в разделе [публикация расширения Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Пакет расширения можно установить только расширения, доступные на [Visual Studio Marketplace](https://marketplace.visualstudio.com/) или [частной коллекции](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Установить пакет расширений в Visual Studio Marketplace

Теперь, когда публикуется расширения, установите его в Visual Studio и протестируйте его.

::: moniker range="vs-2017"

1. В Visual Studio на **средства** меню, щелкните **расширения и обновления**.

::: moniker-end

::: moniker range=">=vs-2019"

1. В Visual Studio на **расширения** меню, щелкните **управляемых расширений**.

::: moniker-end

2. Нажмите кнопку **Online** и выполните поиск «Пакета расширения тестирования».

3. Нажмите **Загрузить**. Расширение и свой список расширений, входящих в пакет расширений будет затем запланировано для установки.

4. Ниже приведено представление загрузки пакет расширений образец **Управление расширениями** диалоговое окно. Если вы хотите установить только некоторые расширения включены в пакет расширений, можно изменить список расширений в **запланировано для установки**.

    ![Загрузить пакет расширения из Marketplace](media/vside-extensionpack.png)

5. Чтобы завершить установку, закройте все экземпляры Visual Studio.

## <a name="remove-the-extension"></a>Удаление расширения

Чтобы удалить расширение с компьютера:

::: moniker range="vs-2017"

1. В Visual Studio на **средства** меню, щелкните **расширения и обновления**.

::: moniker-end

::: moniker range=">=vs-2019"

1. В Visual Studio на **расширения** меню, щелкните **управляемых расширений**.

::: moniker-end

2. Выберите **пакет расширений тестов** и нажмите кнопку **удаления**. Расширение и свой список расширений, входящих в пакет расширений будет затем запланировано для удаления.

3. Чтобы завершить удаление, закройте все экземпляры Visual Studio.
