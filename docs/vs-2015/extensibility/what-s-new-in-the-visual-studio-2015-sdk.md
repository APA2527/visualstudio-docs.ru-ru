---
title: Новые возможности пакета SDK для Visual Studio 2015 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d51474f2e242f764a84edaa9f2712418c859460
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408700"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Что&#39;возможности пакета SDK для Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пакет SDK для Visual Studio имеет следующие новые и обновленные функции для Visual Studio 2015, обновление Visual Studio 2015 и Visual Studio 2017.

## <a name="visual-studio-2017"></a>Visual Studio 2017

Начиная с Visual Studio 2017, сканирование на наличие шаблонов пользовательских проектов и элементов больше не выполняется. Вместо этого расширения необходимо указать файлы манифеста, которые описывают расположение установки из этих шаблонов. Visual Studio 2017 можно использовать, чтобы обновить расширения VSIX. При развертывании расширения с помощью MSI, необходимо создать файлы манифеста шаблонов вручную. Дополнительные сведения см. в разделе [обновление настраиваемых шаблонов проектов и элементов для Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Шаблон манифеста документирована в [Visual Studio шаблон манифеста Справочник по схеме](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="vs-2015-sdk-update-1"></a>Обновления пакета SDK для Visual STUDIO 2015 1
 Обновление 1 включает в себя средства для работы с функцией цветовые темы и службы образов в Visual Studio расширение.

 Эти разделы находятся под [служебные программы VSSDK](../extensibility/internals/vssdk-utilities.md) раздел:

- [Инструменты цветовой разметки тем](../extensibility/internals/color-theming-tools.md) позволяют создавать и изменять собственные цвета для Visual Studio.

- [Средства службы образов](../extensibility/internals/image-service-tools.md) позволяют работать с файлами манифеста изображений Visual Studio.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Новый способ добавить пакет SDK для Visual Studio в Visual Studio
 Начиная с Visual Studio 2015, не нужно отдельно скачать пакет SDK для Visual Studio. Вместо этого его можно установить как часть процесса Обычная установка, или вы можете установить его позже. При открытии или создании решение VSIX, Visual Studio предложит установить средства расширения Visual Studio. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Новые способы создания расширений
 Начиная с пакета SDK для Visual Studio 2015, у вас есть различные параметры для создания расширений, в зависимости от того, какой язык программирования, на который вы используете.

### <a name="visual-c-and-visual-basic"></a>Visual C# и Visual Basic
 Для C# и Visual Basic имеется полный набор шаблонов элементов проекта, которые позволяют создавать пакеты VSPackage, команды меню, окна инструментов, редактор классификаторы, элементов оформления редактора и margin расширения редактора. Можно добавить любые или все из них в стандартный проект VSIX. Дополнительные сведения:

- [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)

- [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md)

- [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [Создание расширения с помощью VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     Мастер VSPackage больше не создает расширения в C# или Visual Basic.

### <a name="c"></a>C++
 Для C++ VSPackage мастер поддерживает команды меню, окна инструментов и специальные редакторы. Искать его в **новый проект** диалоговое окно в **Visual C++ / расширяемости**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>VS SDK ссылочных сборок с помощью NuGet
 Для улучшенной портативности и совместного использования проектов расширения среды можно использовать версии NuGet ссылочных сборок пакета SDK для VS.  Они доступны на [nuget.org](http://www.nuget.org) опубликованное [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) и можно легко добавить в проект или решение с помощью Visual Studio **ссылается на / управление NuGet Пакеты** диалоговое окно. Можно добавить отдельные ссылки на сборки расширяемость для конкретного или добавить VS SDK ссылается на сборки, одновременно с помощью пакета SDK для VS [метапакет](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Дополнительные сведения о NuGet см. в разделе [Обзор NuGet](http://docs.nuget.org/) и [управление пакетами NuGet с помощью диалогового окна](http://docs.nuget.org/Consume/Package-Manager-Dialog).

 При использовании версии NuGet ссылочных сборок пакета SDK для VS, другому пользователю не нужно установить пакет SDK для VS для открытия и сборки проекта.  NuGet ссылочных сборок и средства сборки пакета SDK для VS будет автоматически устанавливаться на компьютере для этого проекта.

 Шаблоны элементов VS SDK используйте NuGet для их ссылки и средства сборки, поэтому вы получаете преимущества NuGet по умолчанию.

> [!NOTE]
> Вы можете использовать ссылочные сборки установлен пакет SDK для VS с проектами (расположенный в \<расположение установки Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) и существующие проекты расширения среды не обязательно должны быть обновлен для использования пакетов NuGet.  Проект **ссылается на / добавить ссылку на** диалогового окна будет продолжать использовать ссылочные сборки установлен пакет SDK для VS.
>
> Если вы хотите изменить существующие проекты для использования NuGet, см. в разделе [как: Миграция пакетов VSPackage в Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) которого имеется раздел об обновлении проектов расширяемости в пакеты NuGet.

## <a name="light-bulbs"></a>Лампочки
 Один из самых замечательных новых способов написания кода для расширения предоставляется в проекте Roslyn. Дополнительные сведения см. в разделе [Roslyn](https://github.com/dotnet/Roslyn).

 Лампочки являются новой возможностью, которая поставляется с VSSDK. Они являются значков, используемых в редакторе Visual Studio, которые разворачиваются для отображения набора действий рефакторинга кода или исправления для проблем, обозначенных в анализаторы встроенный код. Дополнительные сведения см. в разделе [Пошаговое руководство: Отображение предложений лампочки](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Руководство по работе обновленный пользователь
 Разработка новых расширений и компонентов для Visual Studio? Ознакомьтесь с обновленной и развернутом [по работе пользователей Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Вы найдете [цвет маркеров](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [размеры шрифтов](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [спецификации макет диалогового окна](../extensibility/ux-guidelines/layout-for-visual-studio.md)и другие инструкции, необходимые легко интегрировать новый пользовательский Интерфейс с помощью Visual Studio.
