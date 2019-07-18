---
title: Добавление проекта и шаблоны элементов проектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b68c9f4bbaed73603c46fc0beab77a308b8933d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203860"
---
# <a name="adding-project-and-project-item-templates"></a>Добавление проекта и шаблонов элементов проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При создании собственных типов проектов, вы должны предоставить поддержку для добавления новых проектов и элементов проекта с помощью стандарта [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированных диалоговые окна Интегрированной среды разработки. В следующих разделах рассматриваются различные методы для добавления проектов и элементов проектов.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Контекст проекта](../../extensibility/internals/project-context.md)  
 Объясняет, что проект предоставляет основные сведения о контексте для упрощенной среды.  
  
 [Приоритет проекта](../../extensibility/internals/project-priority.md)  
 Объясняет, что элемент проекта обычно является членом одного проекта, чтобы избежать неоднозначности, о том, какие позволяет открыть элемент проекта.  
  
 [Проект прочих файлов](../../extensibility/internals/miscellaneous-files-project.md)  
 Сведения об этих двух типах редакторов, которые могут использоваться для открытия файлов в проекте и в роли, проект играет определить, какой редактор использовать при открытии элемента проекта.  
  
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)  
 Объясняет, что происходит при [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] создается проект.  
  
 [Добавление элементов в диалоговые окна "Добавление новых элементов"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Описание процесса добавления элементов к **Добавление нового элемента** диалоговое окно.  
  
 [Добавление каталогов в диалоговое окно "Создание проекта"](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Предоставляет пример регистрации новый каталог, содержащий пользовательские шаблоны, доступные через VSPackage.  
  
 [Добавление каталогов в диалоговое окно "Добавление новых элементов"](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Предоставляет пример новый набор каталогов для регистрации **Добавление нового элемента** диалоговое окно.  
  
 [Команды, определенные в интегрированной среде разработки, для расширения систем проектов](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Перечислены различные типы элементов команды, используемые для расширения систем проектов.  
  
 [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Перечисляет идентификаторы CATID для объектов, которые используются для расширения [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], и [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] системы проектов.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Практическое руководство. Открытие редакторов соответствующих проектов](../../extensibility/how-to-open-project-specific-editors.md)  
 Содержит пошаговые инструкции по открытию элемент само по себе привязан к определенном редакторе для проекта.  
  
 [Практическое руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)  
 Содержит пошаговые инструкции по открытию стандартного редактора.  
  
 [Подтипы проектов](../../extensibility/internals/project-subtypes.md)  
 Ссылки на концептуальные разделы подтип проекта. Подтипов проекта расширять существующие [!INCLUDE[csprcs](../../includes/csprcs-md.md)] и [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] проектов.  
  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Ссылки на дополнительные разделы, которые содержат сведения о создании новых типов проектов.
