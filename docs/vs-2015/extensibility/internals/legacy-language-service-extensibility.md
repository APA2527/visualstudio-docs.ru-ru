---
title: Расширяемость устаревший языковой службы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 43
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9346311aac4bc5833005423e90c2eb92faddcb84
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194980"
---
# <a name="legacy-language-service-extensibility"></a>Расширяемость языковой службы прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Языковая служба обеспечивает поддержку определенного языка для редактирования исходного кода в интегрированной среде разработки.  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Чтобы подробнее узнать о новых способах реализации языковой службы, см. в разделе [редактора и языковой службы расширения](../../extensibility/editor-and-language-service-extensions.md).  
  
 В этом разделе рассматриваются в структуре и реализации языковой службы прежних версий.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Миграция языковой службы прежних версий](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 В этой статье описывается обновление языковой службы из Visual Studio 2008 до последней версии.  
  
 [Основные компоненты языковой службы прежних версий](../../extensibility/internals/legacy-language-service-essentials.md)  
 Предоставляет важные сведения о разработке языковые службы, которые интегрируются язык программирования в Visual Studio.  
  
 [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Содержит ссылки на разделы, которые помогут вам создать языковую службу.  
  
 [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Сведения о поддержке, выделение синтаксиса в языковой службе.  
  
 [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Сведения об использовании managed package framework (MPF) для реализации полнофункционального языковой службы в управляемом коде.  
  
 [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Описание библиотеки и средства, которые позволяют просматривать представления в виде дерева символов в интегрированной среде разработки.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md)  
 Обзор редакторов Visual Studio.  
  
 [Поддержка языковой службы для отладки](../../extensibility/internals/language-service-support-for-debugging.md)  
 Содержит сведения и ссылки для Visual Studio отладку SDK, который содержит сведения, необходимые для создания и настройки отладчика компоненты, используемые для отладки программ.
