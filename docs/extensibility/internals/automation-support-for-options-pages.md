---
title: Поддержка автоматизации страниц параметров | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81cf358d3dfb8fc45a4f696b0483e28673094d44
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62862034"
---
# <a name="automation-support-for-options-pages"></a>Поддержка автоматизации для страницы параметров
Пакеты VSPackage могут предоставлять пользовательскую **параметры** диалоговых окон для **средства** меню (**Сервис-Параметры** страницы) в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и их можно сделать доступными для модели автоматизации модель.

## <a name="tools-options-pages"></a>Сервис Параметры - страницы
 Чтобы создать **Сервис-Параметры** странице VSPackage необходимо предоставить реализацию пользовательского элемента управления, возвращается в среду через реализацию VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метод. (Или, для управляемого кода, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> метод.)

 Это необязательно, но настоятельно рекомендуется, чтобы разрешить доступ к этой новой странице с помощью модели автоматизации. Это можно сделать, выполнив следующие действия:

1. Расширить <xref:EnvDTE._DTE.Properties%2A> объекта путем реализации производным интерфейса IDispatch объекта.

2. Возвращают реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод (или для управляемого кода <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> метод) на объект производного IDispatch.

3. Когда потребитель автоматизации вызывает <xref:EnvDTE._DTE.Properties%2A> метода в пользовательском **параметр** страницу свойств в среде используется <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод, чтобы получить пользовательский **Сервис-Параметры** автоматизации страницы Реализация.

4. Объект автоматизации из VSPackage затем используется для предоставления каждой <xref:EnvDTE.Property> возвращаемый <xref:EnvDTE._DTE.Properties%2A>.

   Пример реализации пользовательского **Сервис-Параметры** странице, см. в разделе [примеры VSSDK](https://aka.ms/vs2015sdksamples).

## <a name="see-also"></a>См. также
- [Предоставление объектов проекта](../../extensibility/internals/exposing-project-objects.md)