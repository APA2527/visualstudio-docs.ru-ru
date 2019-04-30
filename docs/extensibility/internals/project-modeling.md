---
title: Проект моделирования | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a2ae395d94d76fd2b11de33cc6d5053d8b92432
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62859672"
---
# <a name="project-modeling"></a>Моделирование проекта
Следующий шаг в предоставление автоматизации для проекта заключается в реализации для стандартного проекта объектов: <xref:EnvDTE.Projects> и `ProjectItems` коллекций; `Project` и <xref:EnvDTE.ProjectItem> объекты должны быть удалены и оставшихся объектов, уникальные для вашей реализации. Эти стандартные объекты определяются в файле Dteinternal.h. В образце BscPrj предоставляется реализация стандартные объекты. Эти классы можно использовать в качестве моделей для создания собственных объектов для стандартного проекта, которые стоят side-by-side объектами проекта из других типов проектов.

 Потребитель автоматизации предполагает в том, чтобы иметь возможность вызывать <xref:EnvDTE.Solution>(«`<UniqueProjName>")` и <xref:EnvDTE.ProjectItems> (`n`) где n ― это номер индекса для получения конкретного проекта в решении. Выполнив этот вызов автоматизации заставляет среду для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> на соответствующий проект иерархии, передав в качестве параметра ItemID и VSHPROPID_ExtObject как параметр VSHPROPID VSITEMID_ROOT. `IVsHierarchy::GetProperty` Возвращает `IDispatch` указатель на объект автоматизации, предоставлении базовых `Project` интерфейс, который вы реализовали.

 Ниже приведен синтаксис `IVsHierarchy::GetProperty`.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Проекты размещения вложенности и использовать коллекции для создания групп элементов проекта. Иерархия выглядит следующим образом.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Вложение означает, что <xref:EnvDTE.ProjectItem> объект может быть <xref:EnvDTE.ProjectItems> коллекции, в то же время из-за `ProjectItems` коллекция может содержать вложенные объекты. Базовый проект пример не демонстрирует такого вложения. Путем реализации `Project` объекта, участвовать в древовидной структуре, характеризующий проектирование общей модели автоматизации.

 Автоматизации проектов следует пути на следующей схеме.

 ![Объекты проекта Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") автоматизации проектов

 Если не реализовать `Project` объекта, среде будут по-прежнему возвращать универсальный `Project` объект, который содержит только имя проекта.

## <a name="see-also"></a>См. также
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>