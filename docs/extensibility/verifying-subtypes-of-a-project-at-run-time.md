---
title: Проверка подтипов проекта во время выполнения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ec71ce9be704566640a90c9187abe77f5cc3fe3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62553992"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Проверка подтипов проекта во время выполнения
Пакет VSPackage, который зависит от подтипом пользовательский проект должен включать логику для поиска, которая подтипа таким образом, чтобы выдать сбой корректно Если отсутствует подтип. Ниже показано, как убедиться в наличии указанного подтипа.

### <a name="to-verify-the-presence-of-a-subtype"></a>Чтобы убедиться в наличии подтипа

1. Получить иерархию проекта из проекта и решения объектов как <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объекта, добавив следующий код к VSPackage.

    ```csharp
    EnvDTE.DTE dte;
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));

    EnvDTE.Project project;
    project = dte.Solution.Projects.Item(1);

    IVsSolution solution;
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));

    IVsHierarchy hierarchy;
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);

    ```

2. Иерархии, чтобы привести <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> интерфейс.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Получить список GUID типа проекта путем вызова <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Проверьте список для GUID указанного подтипа.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>См. также
- [Подтипов проекта](../extensibility/internals/project-subtypes.md)
- [Разработка подтипов проекта](../extensibility/internals/project-subtypes-design.md)
- [Свойства и методы, расширенные подтипами проектов](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)