---
title: Практическое руководство. Размещение и упорядочение шаблонов проектов и элементов | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- custom template locations [Visual Studio]
- item templates, locations
- Visual Studio templates, locations
- project templates [Visual Studio], displaying
- templates [Visual Studio], locations
ms.assetid: 71f9ed52-c9c9-4818-9bce-c279ffaa0438
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b5f55de910eb77ec7ccbd205b78d5c95039e6b39
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651874"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Практическое руководство. Размещение и упорядочение шаблонов проектов и элементов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы шаблоны отображались в диалоговых окнах **Новый проект** и **Добавление нового элемента**, файлы шаблонов следует помещать в расположение, которое Visual Studio распознает. Для шаблонов можно создать пользовательские подкатегории, которые также отображаются в пользовательском интерфейсе.

## <a name="locating-templates"></a>Расположение шаблонов
 По умолчанию Visual Studio проверяет два расположения на наличие шаблонов проектов и элементов. Если сжатый файл, содержащий VSTEMPLATE-файл, находится в этих расположениях, шаблон будет отображаться в диалоговом окне **Новый проект** или **Добавление нового элемента**.

### <a name="installed-templates"></a>Установленные шаблоны
 По умолчанию шаблоны, установленные вместе с продуктом, находятся в папке:

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\*язык*\\*языковой стандарт*\

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\*язык*\\*языковой стандарт\\*

  Например, следующий каталог содержит шаблоны проектов [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для английского языка:

  C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\

### <a name="custom-templates"></a>Пользовательские шаблоны
 По умолчанию пользовательские шаблоны расположены в папке:

- \My Documents\Visual Studio *версия*\Templates\ProjectTemplates\\*язык*\

- \My Documents\Visual Studio *версия*\Templates\ItemTemplates\\*язык*\

  Например, следующий каталог содержит настраиваемые шаблоны проектов [!INCLUDE[csprcs](../includes/csprcs-md.md)]:

  C:\Documents and Settings\UserName\My Documents\\<Visual Studio версия\>\Templates\ProjectTemplates\Visual C#\

  Пользовательские шаблоны не включают подкаталог для локализованных шаблонов. Каталог по умолчанию для пользовательских шаблонов можно изменить в диалоговом окне **Параметры** в области **Среда\Проекты и решения**.

## <a name="organizing-templates"></a>Упорядочение шаблонов
 Категории в диалоговых окнах **Новый проект** и **Добавление нового элемента** отражают структуры каталогов, которые существуют в расположениях установленных и пользовательских шаблонов. Можно изменить эти структуры каталогов, чтобы упорядочить шаблоны удобным для вас образом.

> [!NOTE]
> Вы не можете создать новую категорию на уровне языка программирования. Новые категории можно создавать только в рамках каждого отдельного языка.

 Если структуры каталогов для установленных и пользовательских шаблонов для определенного языка не имеют одну и ту же структуру (то есть в одной папке присутствуют каталоги, которые отсутствуют в другой), набор категорий, отображаемых в диалоговом окне **Новый проект**, будет представлять собой слияние всех категорий.

### <a name="organizing-installed-templates"></a>Упорядочение установленных шаблонов
 Вы можете упорядочить установленные шаблоны путем создания подкаталогов в папке языка программирования. Эти подкаталоги отображаются в диалоговых окнах **Новый проект** и **Добавление нового элемента** в виде виртуальных папок в рамках каждого языка.

##### <a name="to-create-new-installed-project-template-categories"></a>Создание новых категорий установленных шаблонов проектов

1. Создайте папку в папке языка, находящейся в каталоге установленных шаблонов. Например, чтобы создать категорию Office для шаблонов проектов [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], необходимо создать следующий каталог:

    \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\VisualBasic\1033\Office\

2. Поместите все шаблоны для этой категории в новую папку.

3. Закройте все экземпляры [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. В меню **Пуск** щелкните **Выполнить**, введите **cmd** и нажмите кнопку **ОК**.

5. В командной строке перейдите в каталог, содержащий файл devenv.exe, и введите **devenv /installvstemplates**.

6. Выполнить команду [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

7. В меню **Файл** последовательно выберите пункты **Создать**и **Проект**.

8. Убедитесь, что категория Office появилась в разделе [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] области **Типы проектов** диалогового окна **Новый проект**.

   Можно также сгруппировать подмножество шаблонов элементов проекта в пользовательской папке.

##### <a name="to-create-new-installed-item-template-categories"></a>Создание новых категорий установленных шаблонов элементов

1. Создайте папку в папке языка, находящейся в каталоге установленных шаблонов. Например, чтобы создать категорию веб-сайтов для шаблонов элементов [!INCLUDE[csprcs](../includes/csprcs-md.md)], необходимо создать следующий каталог:

     \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\CSharp\1033\Web\

2. Поместите все шаблоны для этой категории в новую папку.

3. Закройте все экземпляры [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. В меню **Пуск** щелкните **Выполнить**, введите **cmd** и нажмите кнопку **ОК**.

5. В командной строке перейдите в каталог, содержащий файл devenv.exe, и введите **devenv /setup**.

6. Выполнить команду [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

7. Создайте новый проект или откройте уже имеющийся.

8. В меню **Проект** выберите пункт **Добавить новый элемент**.

9. Убедитесь, что категория веб-сайтов появилась в области **Типы проектов** диалогового окна **Добавление нового элемента**.

### <a name="organizing-custom-templates"></a>Упорядочение пользовательских шаблонов
 Пользовательские шаблоны можно упорядочить по своим собственным категориям путем добавления новых папок в расположение пользовательских шаблонов. Диалоговое окно **Новый проект** отражает все изменения, вносимые в категории шаблонов.

##### <a name="to-create-new-custom-project-template-categories"></a>Создание новых категорий пользовательских шаблонов проектов

1. Создайте папку в папке языка, находящейся в каталоге пользовательских шаблонов проектов. Например, чтобы создать категорию HelloWorld для шаблонов [!INCLUDE[csprcs](../includes/csprcs-md.md)], необходимо создать следующий каталог:

    \My Documents\\<Visual Studio версия\>\Templates\ProjectTemplates\CSharp\HelloWorld\

2. Поместите все шаблоны для этой категории в новую папку.

3. В меню **Файл** последовательно выберите пункты **Создать**и **Проект**.

4. Убедитесь, что категория HelloWorld появилась в разделе [!INCLUDE[csprcs](../includes/csprcs-md.md)] области **Типы проектов** диалогового окна **Новый проект**.

   Можно также сгруппировать подмножество пользовательских шаблонов элементов в пользовательской папке.

##### <a name="to-create-new-custom-item-template-categories"></a>Создание новых категорий пользовательских шаблонов элементов

1. Создайте папку в папке языка, находящейся в каталоге пользовательских шаблонов элементов. Например, чтобы создать категорию HelloWorld для шаблонов [!INCLUDE[csprcs](../includes/csprcs-md.md)], необходимо создать следующий каталог:

     \My Documents\\<Visual Studio версия\>\Templates\ItemTemplates\CSharp\HelloWorld\

2. Поместите все шаблоны для этой категории в новую папку.

3. Создайте новый проект или откройте уже имеющийся.

4. В меню **Проект** выберите пункт **Добавить новый элемент**.

5. Убедитесь, что категория HelloWorld появилась в области **Типы проектов** диалогового окна **Добавление нового элемента**.

### <a name="displaying-templates-in-parent-categories"></a>Отображение шаблонов в родительских категориях
 Можно включить шаблоны в подкатегориях, чтобы они отображались в их родительских категориях, с помощью элемента `NumberOfParentCategoriesToRollUp` в VSTEMPLATE-файле. Эти действия идентичны как для шаблонов проектов, так и для шаблонов элементов.

##### <a name="to-display-templates-in-parent-categories"></a>Отображение шаблонов в родительских категориях

1. Найдите ZIP-файл, содержащий шаблон.

2. Извлеките ZIP-файл.

3. Откройте VSTEMPLATE-файл в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. В элементе `TemplateData` добавьте элемент `NumberOfParentCategoriesToRollUp`. Например, следующий код делает шаблон видимым в родительской категории, но не на более высоких уровнях.

    ```
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

5. Сохраните VSTEMPLATE-файл и закройте его.

6. Выберите файлы в шаблоне, щелкните выбранное правой кнопкой мыши, выберите пункт **Отправить**, а затем пункт **Сжатая ZIP-папка**. Файлы сжимаются в ZIP-файл.

7. Удалите извлеченные файлы шаблона и ZIP-файл старого шаблона.

8. Поместите новый ZIP-файл в каталог, где находился удаленный ZIP-файл.

## <a name="see-also"></a>См. также раздел
 [Настройка шаблонов](../ide/customizing-project-and-item-templates.md) [шаблон Visual Studio Template Справочник](../extensibility/visual-studio-template-schema-reference.md) по [элемент numberofparentcategoriestorollup (шаблоны Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) [как создать шаблоны проектов](../ide/how-to-create-project-templates.md) [руководство: создание шаблонов элементов](../ide/how-to-create-item-templates.md)
