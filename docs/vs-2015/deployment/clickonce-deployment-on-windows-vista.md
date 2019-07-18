---
title: Развертывание ClickOnce в Windows Vista | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e25f9da960b1de8acb1950b2bdd3ab7e61409f17
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675466"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Развертывание ClickOnce в Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Создание приложений в Visual Studio для контроля учетных записей (UAC) на Windows Vista обычно создается внедренный манифест, как двоичные данные в кодировке XML в исполняемый файл приложения. Так как для приложений ClickOnce и COM без регистрации требуется внешний манифест, Visual Studio создает файл для этих типов проектов, содержащий данные UAC вместо внедренного манифеста. По умолчанию Visual Studio использует сведения из файла app.manifest для создания внешнего манифеста UAC (для развертывания ClickOnce и COM без регистрации), или внедрить в исполняемый файл приложения (для всех остальных случаях). Visual Studio предоставляет следующие возможности для создания манифеста:  
  
- Использование внедренного манифеста. Внедрение данных UAC в исполняемый файл приложения и запуск от имени обычного пользователя.  
  
   Это параметр по умолчанию (Если вы не используете ClickOnce). Этот параметр будет поддерживать обычным способом, в котором работает Visual Studio в Windows Vista; то есть создание внутренних и внешних манифеста, с помощью команды `AsInvoker`.  
  
- Использование внешнего манифеста. Создайте внешний манифест с помощью app.manifest.  
  
   Это приводит к возникновению ошибки только внешний манифест, используя сведения в app.manifest. При публикации приложения с помощью ClickOnce или COM без регистрации, Visual Studio добавляет в проект app.manifest и добавляет этот параметр.  
  
- Работа без использования манифеста. Создайте приложение без манифеста.  
  
   Этот подход также называется *виртуализации*. Используйте этот параметр для совместимости с существующими приложениями из более ранних версиях Visual Studio.  
  
  Новые свойства доступны на **приложения** страницы в конструкторе проектов (Visual C# только для проектов) и формат файла проекта MSBuild.  
  
  Обратите внимание на то, что метод настройки создания манифеста контроля учетных Записей в Интегрированной среде разработки Visual Studio отличается в зависимости от типа проекта (Visual C# и Visual Basic).  
  
  Сведения о настройке проектов Visual C# для создания манифеста см. в разделе [Application Page, Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  Сведения о настройке проектов Visual Basic для создания манифеста, см. в разделе [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>См. также  
 [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Разрешения пользователей и Visual Studio](https://msdn.microsoft.com/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
