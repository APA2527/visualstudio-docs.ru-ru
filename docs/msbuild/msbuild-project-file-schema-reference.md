---
title: Справочные сведения о схеме файлов проектов MSBuild | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c49c2198a4ecc40a40e3f5f6414bfd4af47279b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842296"
---
# <a name="msbuild-project-file-schema-reference"></a>Справочные сведения о схеме файлов проектов MSBuild
Представлена таблица, содержащая все элементы XML-схемы [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], доступные атрибуты элементов и дочерние элементы.

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] использует файлы проекта для указания механизму сборки, что собирать и как делать это. Файлы проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] представляют собой XML-файлы, которые подчиняются XML-схеме [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. В данном разделе описывается содержимое файла определений XML-схемы (*XSD*) для [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

## <a name="msbuild-xml-schema-elements"></a>Элементы XML-схемы MSBuild
 В следующей таблице перечислены все элементы XML-схемы [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], а также их дочерние элементы и атрибуты.

|Элемент|Дочерние элементы|Атрибуты|
|-------------|--------------------|----------------|
|[Элемент Choose (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> When|--|
|[Элемент Import (MSBuild)](../msbuild/import-element-msbuild.md)|--|Условие<br /><br /> Проект|
|[Элемент ImportGroup](../msbuild/importgroup-element.md)|Импорт|Условие|
|[Элемент Item (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Условие<br /><br /> Исключить<br /><br /> Включение<br /><br /> Удалить|
|[Элемент ItemDefinitionGroup (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Элемент*|Условие|
|[Элемент ItemGroup (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Элемент*|Условие|
|[Элемент ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Элемент*|Условие|
|[Элемент OnError (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Условие<br /><br /> ExecuteTargets|
|[Элемент Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Нажмите кнопку<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Элемент Output (MSBuild)](../msbuild/output-element-msbuild.md)|--|Условие<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|
|[Элемент Parameter](../msbuild/parameter-element.md)|--|Вывод<br /><br /> ParameterType<br /><br /> Обязательно|
|[Элемент ParameterGroup](../msbuild/parametergroup-element.md)|*Параметр*|--|
|[Элемент Project (MSBuild)](../msbuild/project-element-msbuild.md)|Нажмите кнопку<br /><br /> Импорт<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> целевого объекта<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[Элемент ProjectExtensions (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Элемент Property (MSBuild)](../msbuild/property-element-msbuild.md)|--|Условие|
|[Элемент PropertyGroup (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Property*|Условие|
|[Элемент SDK (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|name<br /><br /> Версия|
|[Элемент Target (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Задача*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Условие<br /><br /> DependsOnTargets<br /><br /> Inputs<br /><br /> KeepDuplicateOutputs<br /><br /> name<br /><br /> Вывод<br /><br /> Returns|
|[Элемент Task (MSBuild)](../msbuild/task-element-msbuild.md)|Вывод|Условие<br /><br /> ContinueOnError<br /><br /> *Параметр*|
|[Элемент TaskBody (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Данные*|Оценка|
|[Элемент UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody|AssemblyFile<br /><br /> AssemblyName<br /><br /> Условие<br /><br /> TaskFactory<br /><br /> TaskName|
|[Элемент When (MSBuild)](../msbuild/when-element-msbuild.md)|Нажмите кнопку<br /><br /> ItemGroup<br /><br /> PropertyGroup|Условие|

## <a name="see-also"></a>См. также
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Условия](../msbuild/msbuild-conditions.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
