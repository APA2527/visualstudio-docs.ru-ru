---
title: Как изменить конфигурацию развертывания SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 74f6377bad0f62aa2c470e72afe64b85b3017ee6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016782"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Как изменить конфигурацию развертывания SharePoint
  Можно создать конфигурацию развертывания или изменить существующую конфигурацию развертывания. Например, можно выполнить один шаг или изменить порядок шагов в процессе развертывания. Может потребоваться создать или изменить конфигурации развертывания, так как встроенные и программно добавленные конфигурации нельзя изменить.

## <a name="create-a-sharepoint-deployment-configuration"></a>Создание конфигурации развертывания SharePoint

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Создание конфигурации развертывания SharePoint

1. В **Обозреватель решений**выберите проект SharePoint, а затем в строке меню выберите **проект**, _имя_проекта_**Свойства**.

2. На вкладке **SharePoint** нажмите кнопку **создать** .

     Откроется диалоговое окно **Добавление новой конфигурации развертывания** .

3. В текстовом поле **имя** введите имя конфигурации развертывания.

4. В области **Доступные шаги развертывания** выберите шаги, которые необходимо добавить в конфигурацию развертывания, нажмите **>** кнопку (), а затем нажмите кнопку **ОК** .

    > [!NOTE]
    > Если вы настроили команду, выполняемую перед развертыванием, или команду, выполняемую после развертывания, эти действия выполняются только в том случае, если они были добавлены в настроенную конфигурацию развертывания.

## <a name="change-the-active-deployment-configuration"></a>Изменение активной конфигурации развертывания

#### <a name="to-change-the-active-deployment-configuration"></a>Изменение активной конфигурации развертывания

1. В **Обозреватель решений**выберите проект SharePoint, а затем в строке меню выберите **Project**  >  ** \<*ProjectName*> Свойства**проекта.

2. Перейдите на вкладку **SharePoint** .

3. В списке **Активная конфигурация развертывания** выберите имя конфигурации развертывания, которую необходимо использовать.

## <a name="see-also"></a>См. также раздел
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
