---
title: Создание пакета решения SharePoint с помощью задачи MSBuild
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 432daff22616950e0a97164190a94082bf2db354
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401499"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Практическое руководство. Создание пакета решения SharePoint с помощью задач MSBuild
  Сборки, очистки и проверки пакета SharePoint ( *.wsp*) с помощью командной строки задачи MSBuild на компьютере разработчика. Эти команды также можно использовать для автоматизации процесса сборки с помощью Team Foundation Server на компьютере построения.

## <a name="build-a-sharepoint-package"></a>Создать пакет SharePoint

#### <a name="to-build-a-sharepoint-package"></a>Чтобы выполнить сборку пакета SharePoint

1. В Windows **запустить** меню, выберите **все программы** > **стандартные** > **командной**.

2. Перейдите в каталог, где находится проект SharePoint.

3. Введите следующую команду, чтобы создать пакет для проекта. Замените *ProjectFileName* с именем проекта.

    ```cmd
    msbuild /t:Package ProjectFileName
    ```

     Например можно выполнить одно из следующих команд, чтобы упаковать проект SharePoint, называется ListDefinition1.

    ```cmd
    msbuild /t:Package ListDefinition1.vbproj
    msbuild /t:Package ListDefinition1.csproj
    ```

## <a name="clean-a-sharepoint-package"></a>Очистить пакет SharePoint

#### <a name="to-clean-a-sharepoint-package"></a>Чтобы очистить пакет SharePoint

1. Откройте окно командной строки.

2. Перейдите в каталог, где находится проект SharePoint.

3. Введите следующую команду, чтобы очистить пакет для проекта. Замените *ProjectFileName* с именем проекта.

    ```cmd
    msbuild /t:CleanPackage ProjectFileName
    ```

     Например можно выполнить одно из следующих команд, чтобы очистить проект SharePoint, называется ListDefinition1.

    ```cmd
    msbuild /t:CleanPackage ListDefinition1.vbproj
    msbuild /t:CleanPackage ListDefinition1.csproj
    ```

## <a name="validate-a-sharepoint-package"></a>Проверить пакет SharePoint

#### <a name="to-validate-a-sharepoint-package"></a>Чтобы проверить пакет SharePoint

1. Откройте окно командной строки.

2. Перейдите в каталог, где находится проект SharePoint.

3. Введите следующую команду, чтобы проверить пакет для проекта. Замените *ProjectFileName* с именем проекта.

    ```cmd
    msbuild /t:ValidatePackage ProjectFileName
    ```

     Например можно выполнить одно из следующих команд для проверки вызывается ListDefinition1 проекта SharePoint.

    ```cmd
    msbuild /t:ValidatePackage ListDefinition1.vbproj
    msbuild /t:ValidatePackage ListDefinition1.csproj
    ```

## <a name="set-properties-in-a-sharepoint-package"></a>Задайте свойства в пакете SharePoint

#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Чтобы задать свойство в пакете SharePoint

1. Откройте окно командной строки.

2. Перейдите в каталог, где находится проект SharePoint.

3. Введите следующую команду, чтобы задать свойство пакета для проекта. Замените *PropertyName* со свойством, которое вы хотите установить.

    ```cmd
    msbuild /property:PropertyName=Value
    ```

     Например вы выполните следующую команду, чтобы установить уровень предупреждений.

    ```cmd
    msbuild /property:WarningLevel = 2
    ```

## <a name="see-also"></a>См. также
- [Создание компонентов SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Практическое руководство. Настройка компонента SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Практическое руководство. Добавление и удаление элементов в компонентах SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
