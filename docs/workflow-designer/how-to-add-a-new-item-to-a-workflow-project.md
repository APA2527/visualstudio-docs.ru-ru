---
title: 'Конструктор рабочих процессов: Добавление нового элемента в проект рабочего процесса'
description: Узнайте, как добавить действия рабочего процесса, конструкторы и другие привычные элементы Visual Studio в проект после создания проекта рабочего процесса.
ms.custom: SEO-VS-2020
ms.date: 06/25/2018
ms.topic: how-to
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e0cc4b24462583a5f704f47c16e6e8d30456512b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938464"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Как добавить новый элемент в проект рабочего процесса

После создания проекта рабочего процесса можно добавить в проект действия рабочего процесса, конструкторы и другие привычные элементы Visual Studio.

В следующей таблице перечислены элементы Windows Workflow Foundation (WF), которые можно добавить в проект рабочего процесса.

| Имя | Описание |
|-| - |
| Действие | Действие, которое составляется из других действий. При выборе этого элемента в проект добавляется тот же файл XAML, что и при выборе шаблона **библиотеки действий** для нового проекта. Дополнительные сведения об этой процедуре см. в разделе [Создание проекта рабочего процесса](creating-a-workflow-project.md). |
| конструктор действий | Конструктор для настройки поведения действия во время разработки. При выборе этого элемента в проект добавляются те же файлы, которые можно получить при выборе шаблона **библиотеки конструктора действий** для нового проекта. |
| CodeActivity | Действие с логикой выполнения, записанное в код. Файл с исходным кодом с переопределением метода <xref:System.Activities.CodeActivity.Execute%2A> уже сформирован. |
| Служба рабочего процесса WCF | Служба [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)], построенная с использованием действий рабочего процесса. При выборе этого элемента в проект добавляются те же файлы, которые можно получить при выборе шаблона **приложения службы рабочего процесса WCF** для нового проекта. Дополнительные сведения об этой процедуре см. [в разделе инструкции. Создание приложения службы рабочего процесса WCF](creating-a-workflow-project.md). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Добавление нового элемента в проект рабочего процесса

1. В меню **Проект** выберите команду **Добавить новый элемент**.

   Откроется диалоговое окно **Добавление нового элемента**.

1. В области слева выберите категорию **Рабочий процесс** и выберите шаблон элемента рабочего процесса.

   > [!NOTE]
   > Если категория **рабочего процесса** не отображается, сначала установите компонент **Windows Workflow Foundation** Visual Studio. Подробные инструкции см. в разделе [Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Введите имя элемента в поле **имя** в нижней части диалогового окна.

1. Нажмите кнопку **Добавить** , чтобы добавить элемент в проект.

## <a name="see-also"></a>См. также раздел

- [Создание проекта рабочего процесса](../workflow-designer/creating-a-workflow-project.md)
