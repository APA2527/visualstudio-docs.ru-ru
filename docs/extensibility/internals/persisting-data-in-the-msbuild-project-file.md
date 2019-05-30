---
title: Сохранение данных в файле проекта MSBuild | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2f09d84d61464b22b9bbe01478f35410bdd0904
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328513"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Сохранение данных в файле проекта MSBuild
Подтип проекта может возникнуть потребность сохранять подтипа данных в файл проекта для последующего использования. Подтип проекта использует сохраняемость файлов в проект для отвечать следующим требованиям:

1. Сохранять данные, используемые в рамках создания проекта. (Дополнительные сведения о Microsoft Build Engine, см. в разделе [MSBuild](../../msbuild/msbuild.md).) Сведения, связанные с построением можете сделать следующее.

    1. Данные, зависящие от конфигурации. То есть данные, хранящиеся в элементы MSBuild с пустым или отсутствующим условия.

    2. Данные, зависящие от конфигурации. То есть данные, хранящиеся в элементы MSBuild, которые являются условие, заданное для конфигурации конкретного проекта. Пример:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Сохранять данные, не имеет значения для построения. Эти данные могут быть выражены в XML произвольной формы, которая не проверяется на соответствие XML-схемы.

    1. Данные, зависящие от конфигурации.

    2. Данные, зависящие от конфигурации.

## <a name="persisting-build-related-information"></a>Сохранение сведений о связанных со сборкой
 Постоянство данных полезно для построения проекта осуществляется через MSBuild. Система MSBuild хранит главную таблицу данных, связанных со сборкой. Для доступа к этим данным для получения и задания значений свойств отвечают подтипов проекта. Подтипов проекта также можно дополнить таблицы данных, связанных со сборкой, путем добавления дополнительных свойств, которые необходимо сохранить и удаление свойств, поэтому они не сохраняются.

 Для изменения данных MSBuild, подтипом проекта отвечает за извлечение из системы базового проекта через объект свойства MSBuild <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> — Это интерфейс, реализованный в системе проектов core и статистической обработки запросов подтип проекта для него, выполнив `QueryInterface`.

 В следующей процедуре описана действия по удалению свойства использования <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Чтобы удалить свойство из файла проекта MSBuild

1. Вызовите `QueryInterface` на <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> подтипа проекта.

2. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> с `pszPropName` задается для свойства, которые требуется удалить.

### <a name="persisting-non-build-related-information"></a>Сохранение связанных сведений о без сборки
 Сохранение данных в файлах проекта, который не имеет значения для построения осуществляется через <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.

 Вы можете реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> в основном `project subtype aggregator` объекта, `project subtype project configuration` объекта, или оба.

 Следующие точки контура основных понятия, касающиеся сохраняемости не сборки связанных элементов данных.

- Базовый проект вызывает в объекте основной проект подтип (то есть внешний проект подтип) средства инвентаризации программного обеспечения для загрузки и сохранения конфигурации независимые данные, и он вызывает на объекты конфигурации проекта подтип проекта для загрузки или сохранения зависящие от конфигурации данные.

- Базовый проект вызывает методы <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> несколько раз для каждого уровня статистической обработки подтип проекта, а также передает идентификатор GUID для каждого уровня.

- Базовый проект передает или получает XML-фрагмент, который выделяется для конкретного проекта подтипом и использует этот механизм как способ сохранения состояния между уровни статистической обработки.

- Базовый проект вызывает подтип внешний проект <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>реализации, передавая идентификатор GUID. Если идентификатор GUID принадлежит подтип внешний проект, он обрабатывает вызов. в противном случае он делегирует вызов внутреннего подтипа проекта и т. д., пока не будет найден соответствующий идентификатор GUID подтипа проекта.

- Подтип проекта можно также изменить XML-фрагмент, до или после он делегирует вызов внутреннего подтипа проекта. В следующем примере показано отрывок из файла проекта, где имя файла, который содержит свойства, относящиеся к подтипу проекта передается в этот подтипа проекта.

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>См. также
- [Подтипы проектов](../../extensibility/internals/project-subtypes.md)