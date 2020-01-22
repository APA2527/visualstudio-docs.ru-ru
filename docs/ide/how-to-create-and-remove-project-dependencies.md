---
title: Практическое руководство. Создание и удаление зависимостей проекта
ms.date: 06/21/2017
ms.topic: conceptual
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
ms.technology: vs-ide-compile
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a286a84d01c6a49b32445106488688ba5b489be
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114544"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Практическое руководство. Создание и удаление зависимостей проекта

При создании решения, содержащего несколько проектов, может потребоваться выполнить сначала сборку отдельных проектов для создания кода, используемого последующими проектами. Когда проект использует исполняемый код, создаваемый другим проектом, последний называется зависимостью первого. Такие отношения зависимости можно определить в диалоговом окне **Зависимости проектов**.

## <a name="to-assign-dependencies-to-projects"></a>Назначение зависимостей проектам

1. Выберите проект в **обозревателе решений**.

2. В меню **Проект** выберите пункт **Зависимости проектов**.

    Открывается диалоговое окно **Зависимости проектов**.

   > [!NOTE]
   > Параметр **Зависимости проектов** доступен только в решении с несколькими проектами.

3. На вкладке **Зависимости** выберите проект из раскрывающегося меню **Проект**.

4. В поле **Зависит от** установите флажок для любого другого проекта, сборка которого должна быть выполнена раньше, чем сборка данного проекта.

   Для создания зависимостей проектов решение должно состоять из нескольких проектов.

## <a name="to-remove-dependencies-from-projects"></a>Удаление зависимостей проектов

1. Выберите проект в **обозревателе решений**.

2. В меню **Проект** выберите пункт **Зависимости проектов**.

     Открывается диалоговое окно **Зависимости проектов**.

    > [!NOTE]
    > Параметр **Зависимости проектов** доступен только в решении с несколькими проектами.

3. На вкладке **Зависимости** выберите проект из раскрывающегося меню **Проект**.

4. В поле **Зависит от** снимите флажки для тех проектов, которые более не являются зависимостями данного проекта.

## <a name="see-also"></a>См. также

- [Создание и очистка проектов и решений в Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Компиляция и сборка](../ide/compiling-and-building-in-visual-studio.md)
- [Общие сведения о конфигурациях построения](../ide/understanding-build-configurations.md)
- [Управление свойствами проектов и решений](managing-project-and-solution-properties.md)
