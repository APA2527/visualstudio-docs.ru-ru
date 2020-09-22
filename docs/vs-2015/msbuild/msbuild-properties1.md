---
title: Properties1 MSBuild | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, properties
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2399ff36639732f20babef368a1d9e2f6758a1c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842909"
---
# <a name="msbuild-properties1"></a>Properties1 MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Свойства представляют собой пары "имя-значение", с помощью которых выполняется настройка сборок. Свойства используются для передачи значений задачам, проверки условий и хранения значений, на которые можно давать ссылки в файле проекта.  
  
## <a name="defining-and-referencing-properties-in-a-project-file"></a>Определение свойств и указание ссылок на них в файле проекта  
 Для объявления свойства создается элемент с таким же именем как у свойства, который является дочерним по отношению к элементу [PropertyGroup](../msbuild/propertygroup-element-msbuild.md). Например, в следующем XML-коде создается свойство `BuildDir` со значением `Build`.  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 Для обращения к свойствам в файле проекта используется синтаксис $(`PropertyName`). В предыдущем примере обращение к свойству осуществляется с помощью оператора $(BuildDir).  
  
 Значения свойств можно изменить путем переопределения свойств. Для свойства `BuildDir` можно задать новое значение, используя следующий XML-код:  
  
```  
<PropertyGroup>  
    <BuildDir>Alternate</BuildDir>  
</PropertyGroup>  
```  
  
 Свойства оцениваются в том порядке, в каком они указаны в файле проекта. Новое значение для `BuildDir` должно быть объявлено после присвоения прежнего значения.  
  
## <a name="reserved-properties"></a>Зарезервированные свойства  
 MSBuild резервирует некоторые имена свойств для хранения сведений о файле проекта и двоичных файлах MSBuild. Обращение к этим свойствам, так же как и к другим свойствам, осуществляется с помощью символа $. Например, оператор $(MSBuildProjectFile) возвращает полное имя файла проекта, включая расширение.  
  
 Дополнительные сведения см. в разделе [инструкции. ссылка на имя или расположение файла проекта](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) , а [также зарезервированные и стандартные свойства MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="environment-properties"></a>Свойства среды  
 Обращаться к переменным среды в файлах проектов можно так же как к зарезервированным свойствам. Например, чтобы использовать переменную среды `PATH` в файле проекта, укажите оператор $(Path). Если проект содержит определение свойства с тем же именем, что и у свойства среды, свойство в проекте переопределит значение переменной среды.  
  
 Каждый проект MSBuild содержит изолированный блок среды. Он видит только чтения из своего блока и записи в него.  MSBuild считывает переменные среды только при инициализации коллекции свойств. Это происходит до оценки файла проекта или его сборки. Кроме того, свойства среды являются статическими. Это значит каждый порожденное средство запускается с теми же именами и значениями.  
  
 Чтобы получить текущее значение переменных среды в порожденном средстве, используйте [функции свойств](../msbuild/property-functions.md) System. Environment. GetEnvironmentVariable. Однако рекомендуется использовать параметр задачи <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>. Свойства среды, заданные в этом массиве строк, могут быть переданы в порожденное средство без изменения переменных среды.  
  
> [!TIP]
> Не все переменные среды считываются в качестве исходных свойств. Все переменные среды, имена которых не являются допустимыми именами свойств MSBuild, например "386", игнорируются.  
  
 Дополнительные сведения см. в разделе [инструкции. Использование переменных среды в сборке](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
## <a name="registry-properties"></a>Свойство реестра  
 Значения разделов системного реестра можно считывать, используя следующий синтаксис. Здесь `Hive` — это куст реестра (например, HKEY_LOCAL_MACHINE), `Key` — имя раздела, `SubKey` — имя подраздела, `Value` — значение подраздела.  
  
```  
$(registry:Hive\MyKey\MySubKey@Value)  
```  
  
 Чтобы получить значение подраздела по умолчанию, опустите `Value`.  
  
```  
$(registry:Hive\MyKey\MySubKey)  
```  
  
 Это значение раздела реестра можно использовать для инициализации свойства сборки. Например, чтобы создать свойство сборки, которое представляет домашнюю страницу веб-браузера Visual Studio, используйте следующий код:  
  
```  
<PropertyGroup>  
  <VisualStudioWebBrowserHomePage>  
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\WebBrowser@HomePage)  
  </VisualStudioWebBrowserHomePage>  
<PropertyGroup>  
```  
  
## <a name="global-properties"></a>Глобальные свойства  
 MSBuild позволяет задавать свойства в командной строке с помощью параметра **/Property** (или **/p**). Эти значения глобальных свойств переопределяют значения свойств, заданные в файле проекта. Это относится также к свойствам среды за исключением зарезервированных свойств, которые нельзя изменить.  
  
 В следующем примере показано, как присвоить глобальному свойству `Configuration` значение `DEBUG`.  
  
```  
msbuild.exe MyProj.proj /p:Configuration=DEBUG  
```  
  
 Кроме того, глобальные свойства можно задавать или изменять для дочерних проектов в сборках из нескольких проектов, используя атрибут `Properties` задачи MSBuild. Дополнительные сведения см. в разделе [Task MSBuild](../msbuild/msbuild-task.md).  
  
 Если свойство задается с помощью атрибута `TreatAsLocalProperty` в теге проекта, это значение глобального свойства не переопределяет значение свойства, заданное в файле проекта. Дополнительные сведения см. в статьях [элемент Project (MSBuild)](../msbuild/project-element-msbuild.md) и [инструкции: построение одних и тех же исходных файлов с разными параметрами](../msbuild/how-to-build-the-same-source-files-with-different-options.md).  
  
## <a name="property-functions"></a>Функции свойств  
 Начиная с .NET Framework версии 4, для оценки сценариев MSBuild можно использовать функции свойств. Получить системное время, сравнить строки, проверить регулярные выражения и выполнить другие действия можно в сценарии сборки без использования задач MSBuild.  
  
 Для работы с любым значением свойства можно использовать методы строки (экземпляра), а также можно вызывать статические методы многих системных классов. Например, чтобы установить для свойства сборки в качестве значения сегодняшнюю дату, сделайте следующее.  
  
```  
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>  
```  
  
 Дополнительные сведения и список функций свойств см. в разделе [функции свойств](../msbuild/property-functions.md).  
  
## <a name="creating-properties-during-execution"></a>Создание свойств во время выполнения  
 Значения свойствам, находящимся за пределами элементов `Target`, присваиваются на этапе оценки сборки. На следующем этапе выполнения свойства могут быть созданы и их значения могут быть изменены следующим образом.  
  
- Свойство может создано любой задачей. Для создания свойства элемент [Задача](../msbuild/task-element-msbuild.md) должен иметь дочерний элемент [Выходные данные](../msbuild/output-element-msbuild.md) с атрибутом `PropertyName`.  
  
- Свойство может создано задачей [CreateProperty](../msbuild/createproperty-task.md). Этот способ не рекомендуется использовать.  
  
- Начиная с версии .NET Framework 3.5, элементы `Target` могут содержать элементы `PropertyGroup`, которые могут содержать объявления свойств.  
  
## <a name="storing-xml-in-properties"></a>Сохранение XML-кода в свойствах  
 Свойства могут содержать произвольный XML-код, предназначенный для передачи значений задачам или отображения сведений из журналов. В следующем примере показано свойство `ConfigTemplate`, которое имеет значение, содержащее XML-код и ссылки на другие свойства. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] заменяет ссылки на свойства соответствующими значениями свойств. Значения свойств присваиваются в том порядке, в каком они появляются. Таким образом, в этом примере `$(MySupportedVersion)`, `$(MyRequiredVersion)` и `$(MySafeMode)` должны быть уже определены.  
  
```  
  
<PropertyGroup>  
    <ConfigTemplate>  
        <Configuration>  
            <Startup>  
                <SupportedRuntime  
                    ImageVersion="$(MySupportedVersion)"  
                    Version="$(MySupportedVersion)"/>  
                <RequiredRuntime  
                    ImageVersion="$(MyRequiredVersion)  
                    Version="$(MyRequiredVersion)"  
                    SafeMode="$(MySafeMode)"/>  
            </Startup>  
        </Configuration>  
    </ConfigTemplate>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](msbuild.md)  
 [Как использовать переменные среды в сборке](../msbuild/how-to-use-environment-variables-in-a-build.md)   
 [Руководство. ссылка на имя или расположение файла проекта](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)   
 [Как создавать одни и те же исходные файлы с разными параметрами](../msbuild/how-to-build-the-same-source-files-with-different-options.md)   
 [Зарезервированные и хорошо известные свойства MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)   
 [Элемент Property (MSBuild)](../msbuild/property-element-msbuild.md)
