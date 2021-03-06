---
title: Элемент SDK (MSBuild) | Документация Майкрософт
description: Сведения о синтаксисе, атрибутах и элементах для элемента Sdk MSBuild, который позволяет создать ссылку на пакет SDK проекта MSBuild.
ms.custom: SEO-VS-2020
ms.date: 01/25/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b348cf2af76c439a28bbb58c0050cc3d458d5457
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048359"
---
# <a name="sdk-element-msbuild"></a>Элемент SDK (MSBuild)

Ссылки на пакет SDK проекта MSBuild.

 \<Project> \<Sdk>

## <a name="syntax"></a>Синтаксис

```xml
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты

 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Name`|Обязательный атрибут.<br /><br /> Имя пакета SDK для проекта.|
|`Version`|Необязательный атрибут.<br /><br /> Версия пакета SDK для проекта.|

### <a name="child-elements"></a>Дочерние элементы

 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

| Элемент | Описание |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Обязательный корневой элемент файла проекта MSBuild. |

## <a name="see-also"></a>См. также раздел

- [How to: Use MSBuild Project SDKs](../msbuild/how-to-use-project-sdk.md) (Практическое руководство. Использование пакета SDK проекта MSBuild)
- [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
