---
title: Пошаговое руководство. Создание настраиваемого действия рабочего процесса сайта | Документация Майкрософт
description: В этом пошаговом руководстве описано, как создать настраиваемое действие для рабочего процесса SharePoint на уровне сайта с помощью Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f2b722ccef084286287b9825c43fa9069f64dcc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937723"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Пошаговое руководство: Создание пользовательского действия рабочего процесса сайта
  В этом пошаговом руководстве показано, как создать настраиваемое действие для рабочего процесса уровня сайта с помощью [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . (Рабочие процессы на уровне сайта применяются ко всему сайту, а не только к списку на сайте.) Настраиваемое действие создает список объявлений резервной копии, а затем копирует в него содержимое списка объявлений.

 В этом пошаговом руководстве описаны следующие задачи.

- Создание рабочего процесса на уровне сайта.

- Создание настраиваемого действия рабочего процесса.

- Создание и удаление списка SharePoint.

- Копирование элементов из одного списка в другой.

- Отображение списка на панели быстрого запуска.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- Поддерживаемые выпуски [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] и SharePoint.

- приведенному.

## <a name="create-a-site-workflow-custom-activity-project"></a>Создание проекта настраиваемого действия рабочего процесса сайта
 Сначала создайте проект для хранения и тестирования настраиваемого действия рабочего процесса.

#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Создание проекта настраиваемого действия рабочего процесса сайта

1. В строке меню выберите **файл**  >  **создать**  >  **проект** , чтобы открыть диалоговое окно **Новый проект** .

2. Разверните узел **SharePoint** под управлением **Visual C#** или **Visual Basic**, а затем выберите узел **2010** .

3. В области **шаблоны** выберите шаблон **проекта SharePoint 2010** .

4. В поле **имя** введите **аннаунцементбаккуп**, а затем нажмите кнопку **ОК** .

     Откроется **Мастер настройки SharePoint** .

5. На странице **Укажите сайт и уровень безопасности для отладки** выберите параметр **Развернуть как решение фермы** , а затем нажмите кнопку **Готово** , чтобы принять уровень доверия и сайт по умолчанию.

     На этом шаге устанавливается уровень доверия для решения в качестве решения фермы — единственный доступный параметр для проектов рабочих процессов.

6. В **Обозреватель решений** выберите узел проекта, а затем в строке меню выберите **проект**  >  **Добавить новый элемент**.

7. В **Visual C#** или **Visual Basic** разверните узел **SharePoint** , а затем выберите узел **2010** .

8. В области **шаблоны** выберите шаблон **последовательный рабочий процесс (только для решения фермы)** , а затем нажмите кнопку **добавить** .

     Откроется **Мастер настройки SharePoint** .

9. На странице **Указание имени рабочего процесса для отладки** примите имя по умолчанию (Аннаунцементбаккуп-Workflow1). Измените тип шаблона рабочего процесса на **Рабочий процесс сайта**, а затем нажмите кнопку **Далее** .

10. Нажмите кнопку **Готово** , чтобы принять остальные параметры по умолчанию.

## <a name="add-a-custom-workflow-activity-class"></a>Добавление класса настраиваемого действия рабочего процесса
 Затем добавьте в проект класс, содержащий код для настраиваемого действия рабочего процесса.

#### <a name="to-add-a-custom-workflow-activity-class"></a>Добавление класса настраиваемого действия рабочего процесса

1. В строке меню выберите **проект**  >  **Добавить новый элемент** , чтобы открыть диалоговое окно **Добавление нового элемента** .

2. В древовидном представлении **Установленные шаблоны** выберите узел **код** , а затем выберите шаблон **класса** в списке шаблонов элементов проекта. Используйте имя по умолчанию Class1. Выберите кнопку **Добавить**.

3. Замените весь код в Class1 следующим кодом:

     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]

4. Сохраните проект, а затем в строке меню выберите **Сборка**  >  **собрать решение**.

     Class1 отображается как настраиваемое действие в **области элементов** на вкладке **компоненты аннаунцементбаккуп** .

## <a name="add-the-custom-activity-to-the-site-workflow"></a>Добавление настраиваемого действия в рабочий процесс сайта
 Затем добавьте действие в рабочий процесс, чтобы оно содержало пользовательский код.

#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Добавление настраиваемого действия в рабочий процесс сайта

1. Откройте представление Workflow1 в конструкторе рабочих процессов в режиме конструктора.

2. Перетащите Class1 с **панели элементов** , чтобы он появился под `onWorkflowActivated1` действием, или откройте контекстное меню для Class1, выберите **Копировать**, откройте контекстное меню для строки под `onWorkflowActivated1` действием и выберите **Вставить**.

3. Сохраните проект.

## <a name="test-the-site-workflow-custom-activity"></a>Тестирование настраиваемого действия рабочего процесса сайта
 Затем запустите проект и запустите рабочий процесс сайта. Настраиваемое действие создает список объявлений для резервного копирования и копирует содержимое из списка извещений в него. Код также проверяет, существует ли уже резервный список, прежде чем создавать его. Если список резервных копий уже существует, он удаляется. Код также добавляет ссылку на новый список на панели быстрого запуска сайта SharePoint.

#### <a name="to-test-the-site-workflow-custom-activity"></a>Тестирование настраиваемого действия рабочего процесса сайта

1. Нажмите клавишу **F5** , чтобы запустить проект и развернуть его в SharePoint.

2. На панели быстрого запуска щелкните ссылку **списки** , чтобы отобразить все списки, доступные на сайте SharePoint. Обратите внимание, что для объявлений с именами **объявлений** существует только один список.

3. В верхней части веб-страницы SharePoint выберите ссылку **рабочие процессы сайта** .

4. В разделе Запуск нового рабочего процесса выберите ссылку **аннаунцементбаккуп-Workflow1** . Это приведет к запуску рабочего процесса сайта и выполнению кода в настраиваемом действии.

5. На панели быстрого запуска выберите ссылку **извещения для резервного копирования** . Обратите внимание, что все объявления, содержащиеся в списке **извещений** , скопированы в этот новый список.

## <a name="see-also"></a>См. также раздел
- [Практическое руководство. Создание приемника событий](../sharepoint/how-to-create-an-event-receiver.md)
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
