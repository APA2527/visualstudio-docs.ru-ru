---
title: Эффективное использование памяти при сборке больших проектов | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af61c15c8ef65c062c1aab6eba079c613f99b5f8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595235"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Эффективное использование памяти при построении больших проектов
Большие проекты часто содержат множество подпроектов и других зависимостей, которые могут занимать большой объем системной памяти во время сборки. При уменьшении доступной системной памяти может снижаться и производительность системы. Ранее старые версии проектов [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] оставались в памяти. В версии 3.5 старые версии проектов удаляются, но результаты сборки сохраняются в кэше, чтобы их можно было получить в дальнейшем.

 Версия 4.0 осуществляет подобное управление памятью автоматически, устраняя потребность в использовании для проектов таких свойств, как `UnloadProjectsOnCompletion` и `UseResultsCache`.

### <a name="see-also"></a>См. также
- [Параллельная сборка нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
