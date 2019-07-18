---
title: Параметры и страницы параметров | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c336503b80e2af34ac58c7debde16895d7f2585
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314852"
---
# <a name="options-and-options-pages"></a>Параметры и страницы параметров
Щелкнув **параметры** на **средства** откроется меню **параметры** диалоговое окно. Параметры в этом диалоговом окне Собирательно называются страницы параметров. Дерево в области навигации включает параметры категории, и каждая категория имеет страницы параметров. При выборе страницы ее содержимое отображается в области справа. Эти страницы позволяют изменить значения параметров, которые определяют состояния пакета VSPackage.

## <a name="support-for-options-pages"></a>Поддержка страниц параметров
 <xref:Microsoft.VisualStudio.Shell.Package> Класс обеспечивает поддержку для создания страниц параметров и параметров категорий. <xref:Microsoft.VisualStudio.Shell.DialogPage> Класс реализует страницы параметров.

 Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage> предлагает пользователю в виде универсального сетки свойств общих свойств. Это поведение можно настроить путем переопределения методов, на странице, чтобы создать пользовательские параметры страницу, которая имеет свой собственный пользовательский интерфейс (UI). Дополнительные сведения см. в разделе [Создание страницы параметров](../../extensibility/creating-an-options-page.md).

 <xref:Microsoft.VisualStudio.Shell.DialogPage> Класс реализует <xref:Microsoft.VisualStudio.Shell.IProfileManager>, который обеспечивает сохраняемость для страницы параметров, а также для пользовательских параметров. Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> и <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> методы сохранения изменений свойств в раздел реестра пользователя, если свойство может быть преобразован в строку и наоборот.

## <a name="options-page-registry-path"></a>Путь в реестре параметры страницы
 По умолчанию путь в реестре свойств, управляемых этим страница параметров определяется объединением <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, word DialogPage и имя типа класса страницы параметров. Например класс страницы параметров могут быть определены следующим образом.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 Если <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> является HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, а затем пар имен и значений свойств — это подразделы HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ Company.OptionsPage.OptionsPageGeneral.

 Путь в реестре сама страница параметров определяется объединением <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, параметры, слово и ToolsOptionsPages странице категории и имени. Например, если параметры настраиваемой страницы имеет категорию, Мои страницы параметров и <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> — HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, а затем на странице параметров имеет раздел реестра, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ Pages\Custom VisualStudio\8.0Exp\ToolsOptionsPages\My параметр.

## <a name="toolsoptions-page-attributes-and-layout"></a>Сервис/Параметры атрибуты страницы и макет
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Атрибут определяет группирование пользовательских страниц параметров в категории в дереве навигации окна **параметры** диалоговое окно. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Атрибут связывает страницу параметров с пакетом VSPackage, предоставляющий интерфейс. Рассмотрим следующий фрагмент кода:

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 Этот код объявляет, что MyPackage предоставляет две страницы параметров, OptionsPageGeneral и OptionsPageCustom. В **параметры** диалоговом окне обоих параметров страницы отображаются **Мои страницы параметров** категории как **Общие** и **Custom**, соответственно.

## <a name="option-attributes-and-layout"></a>Атрибуты параметра и макет
 Пользовательский интерфейс (UI), предоставляющий страницы определяет внешний вид параметров на странице настраиваемых параметров. Макета, добавления меток и описание параметров на странице универсальные параметры определяются следующие атрибуты:

- <xref:System.ComponentModel.CategoryAttribute> Определяет категорию параметра.

- <xref:System.ComponentModel.DisplayNameAttribute> Определяет отображаемое имя параметра.

- <xref:System.ComponentModel.DescriptionAttribute> Определяет описание параметра.

  > [!NOTE]
  > Эквивалентное атрибуты, SRCategory, LocDisplayName и SRDescription, использование строковых ресурсов для локализации и определяются в [образец управляемого проекта](http://go.microsoft.com/fwlink/?LinkId=122774).

  Рассмотрим следующий фрагмент кода:

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  Параметр OptionInteger отображается на странице "Параметры", как **целочисленный параметр** в **параметры** категории. Если параметр выбран, описание, **моей целочисленный параметр**, отображается в поле «Описание».

## <a name="accessing-options-pages-from-another-vspackage"></a>Доступ к страниц параметров из другого пакета VSPackage
 Пакет VSPackage, который содержит и администрирует страницы параметров можно получить доступ программными средствами из другого пакета VSPackage с помощью модели автоматизации. Например в следующем коде VSPackage регистрируется как размещение страницы параметров.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 В следующем фрагменте кода получает значение OptionInteger из MyOptionPage:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 Когда <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> атрибут регистрирует страницу параметров, страница регистрируется в разделе ключей if AutomationProperties `SupportsAutomation` аргумент атрибута — `true`. Автоматизация проверяет этот параметр реестра для поиска связанных VSPackage и автоматизации, а затем обращается к свойству через размещенной страницу параметров, в данном случае Моя страница «Сетка».

 Путь в реестре свойство автоматизации определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, параметры, слово и AutomationProperties странице категории и имени. Например, если страницы параметров имеет категорию "My Category", имя мою страницу сетки и <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, то свойство автоматизации имеет раздел реестра, HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\VisualStudio\8.0Exp\AutomationProperties\My страница Category\My «сетка».

> [!NOTE]
> Каноническое имя, Мои Category.My страница «Сетка», — значение подраздела имя этого ключа.