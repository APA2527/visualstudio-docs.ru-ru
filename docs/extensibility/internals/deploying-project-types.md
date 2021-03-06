---
title: Развертывание типов проектов | Документация Майкрософт
description: Узнайте, как развертывать типы проектов с управляемым кодом с помощью нового агрегатора типа проекта и установщик Windows пакета для повторного распространения в пакете SDK для Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1b015f29b6521482013a77bbcf7c44d8a79afa6
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329884"
---
# <a name="deploy-project-types"></a>Развертывание типов проектов
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] устанавливает новый агрегатор типа проекта (*ProjectAggregator2.dll*), а также пакет установщик Windows для распространения (*ProjectAggregator2.msi*). Для типов проектов с управляемым кодом необходимо использовать новый агрегатор. ProjectAggregator2 работает с ограничениями в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] агрегаторе проекта, что предотвращает неправильную работу типов проектов управляемого кода. Следующие шаги описывают, как изменить пакет VSPackage для использования новой агрегаторы.

1. Удалите проект Нативехиерарчивраппер из решения.

2. Удалите из программы установки все двоичные файлы Нативехиерарчивраппер.

3. Добавьте *ProjectAggregator2.msi* в программу установки.
