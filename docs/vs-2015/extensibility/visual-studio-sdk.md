---
title: Пакет SDK для Visual Studio | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c338648ebb69874781906c0eabff670e5158be8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538802"
---
# <a name="visual-studio-sdk"></a>SDK для Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пакет SDK для Visual Studio поможет вам расширить возможности Visual Studio или интегрировать новые возможности в Visual Studio. Вы можете предоставлять свои расширения другим пользователям, а также в коллекции Visual Studio. Ниже перечислены некоторые из способов расширения Visual Studio:  
  
- Добавление команд, кнопки, меню и других элементов пользовательского интерфейса в интегрированную среду разработки  
  
- Как добавить окна средств для новых функциональных возможностей  
  
- Расширения IntelliSense для данного языка и обеспечивает поддержку технологии IntelliSense для новых языков программирования  
  
- Использование значка лампочки для предоставления подсказки и рекомендации, помогающие разработчикам создавать более качественные приложения  
  
- Включить поддержку нового языка  
  
- Добавление пользовательского типа проекта  
  
- Миллионы разработчиков с помощью Visual Studio Marketplace  
  
  Если вы не написали ни расширение Visual Studio, прежде чем, вы увидите Дополнительные сведения об этих функциях, а также в [начинается разработка расширений Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Установка пакета SDK для Visual Studio  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Новые возможности пакета SDK для Visual Studio 2015  
 Пакет SDK для Visual Studio имеет ряд новых возможностей, включая лампочки и новых элементов проекта, которые позволяют создавать команды меню, окна инструментов и расширения редактора, с помощью пакета VSIX. Дополнительные сведения см. в разделе [новые возможности пакета SDK для Visual Studio 2015](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Руководство по работе пользователей Visual Studio  
 Полезные советы по проектированию пользовательского интерфейса для расширения в [по работе пользователей Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Вы также узнаете, как осуществлять расширение отлично выглядят на высоким значением dpi с нашей [адресации проблем с разрешением ЭКРАНА](../extensibility/addressing-dpi-issues2.md) раздела.  
  
 Воспользоваться преимуществами [каталог и служба образов](../extensibility/image-service-and-catalog.md) управления отличный образами и поддержку высокое разрешение и темы.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Поиск и установку существующие расширения Visual Studio  
 Вы найдете расширений Visual Studio в **расширения и обновления** диалоговое окно на **средства** меню. Дополнительные сведения см. в разделе [Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Также можно найти расширения в [Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Справочник по пакету SDK для Visual Studio  
 Вы найдете ссылку на API пакета SDK для Visual Studio по [Справочник по Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Примеры Visual Studio SDK  
 Примеры открытым исходным кодом расширений VS SDK можно найти на сайте GitHub в [примеры Visual Studio](https://aka.ms/vs2015sdksamples). Этот репозиторий GitHub содержит примеры, демонстрирующие различные расширяемые возможности в Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Другие ресурсы пакета SDK для Visual Studio  
 Если у вас вопросы о VSSDK или хотите поделиться опытом разработки расширений, можно использовать [форум расширяемости Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) или [ExtendVS Group Chat](https://gitter.im/Microsoft/extendvs).  
  
 Можно найти дополнительные сведения в [VSX Arcana блог](http://blogs.msdn.com/b/vsx/) и номер блогов, написанные специалистами MVP:  
  
- [Расширения избранные Visual Studio](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
- [Расширяемость Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
- [Расширение Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>См. также  
 [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Практическое руководство. Перенос проектов расширяемости в Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [Часто задаваемые вопросы. Преобразование надстроек в расширения VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Управление несколькими потоками в управляемом коде](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)   
 [Добавление команд на панели инструментов](../extensibility/adding-commands-to-toolbars.md)   
 [Расширение и настройка средства Windows](../extensibility/extending-and-customizing-tool-windows.md)   
 [Редактор и расширения службы языка](../extensibility/editor-and-language-service-extensions.md)   
 [Расширение проектов](../extensibility/extending-projects.md)   
 [Расширение пользовательские настройки и параметры](../extensibility/extending-user-settings-and-options.md)   
 [Создание пользовательских проектов и шаблонов элементов](../extensibility/creating-custom-project-and-item-templates.md)   
 [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md)   
 [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Использование и предоставление служб](../extensibility/using-and-providing-services.md)   
 [Расширение подключенной службы](../extensibility/extending-connected-services.md)   
 [Управление пакетами VSPackage](../extensibility/managing-vspackages.md)   
 [Изолированная оболочка Visual Studio](../extensibility/visual-studio-isolated-shell.md)   
 [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Внутри Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Поддержка пакета SDK для Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Архив](../extensibility/archive.md)   
 [Справочник по пакету SDK для Visual Studio](../extensibility/visual-studio-sdk-reference.md)
