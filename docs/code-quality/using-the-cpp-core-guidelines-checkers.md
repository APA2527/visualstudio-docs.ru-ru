---
title: Использование средств проверки на соответствие C++ Core Guidelines
ms.date: 08/14/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
dev_langs:
- CPP
ms.openlocfilehash: 7d888204de33ba870111be08ae91bb09d09416d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62820941"
---
# <a name="use-the-c-core-guidelines-checkers"></a>Использование средств проверки на соответствие C++ Core Guidelines

C++ Core Guidelines представляют собой переносимый набор рекомендации, правила и рекомендации о написании кода на C++, созданные экспертами C++ и конструкторы. В настоящее время Visual Studio поддерживает подмножество этих правил как часть его средств анализа кода для C++. Средства проверки рекомендация core устанавливаются по умолчанию в Visual Studio 2017 и Visual Studio 2019 и являются [предоставляется в виде пакета NuGet для Visual Studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Проект C++ Core Guidelines

Создан (Bjarne Stroustrup) и другими C++ Core Guidelines — это руководство по использованию современный C++, безопасно и эффективно. Рекомендации подчеркнуть статический строгая типизация и безопасность ресурсов. Они определять способы устранить или свести к минимуму наиболее подверженных ошибкам части языка и предлагают способы сделать код более простой и более высокую производительность надежным способом. Эти рекомендации обслуживаются Standard C++ Foundation. Дополнительные сведения см. в документации [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)и получить доступ к документации файлов проекта C++ Core Guidelines на [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Включить правила C++ Core Check в анализе кода
 Вы можете включить анализ кода в проекте, выбрав **включить анализ кода в построении** флажок в **анализа кода** раздел **страницы свойств** диалоговое окно для ваш проект.

 ![Страница свойств для параметров общие анализа кода](media/cppcorecheck_codeanalysis_general.png)

 Подмножество правила C++ Core Check включается в собственный рекомендуемые Майкрософт набор правил, который выполняется по умолчанию при включении анализа кода. Чтобы включить дополнительные правила Core Check, щелкните раскрывающийся список и выберите какие наборы правил, которые необходимо включить:

 ![Раскрывающийся список для дополнительных наборов правил для C++ Core Check](media/cppcorecheck_codeanalysis_extensions.png)

## <a name="examples"></a>Примеры
 Вот некоторые из проблем, которые можно найти правила C++ Core Check примером:

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

В этом примере показаны некоторые из предупреждений, которые можно найти правила C++ Core Check:

- C26494 — правило Type.5. Всегда Инициализируйте объект.

- C26485 — правило Bounds.3. Нет отхода массива в указатель.

- C26481 — правило Bounds.1. Не используйте арифметику указателей. Взамен рекомендуется использовать `span`.

Если установлены и включены при компиляции кода C++ Core Check наборы правил анализа кода, первые два предупреждения выводятся, но третий подавляется. Ниже приведен результат сборки из образца кода.

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

C++ Core Guidelines должны помогать вам в написании кода лучше и безопаснее. Тем не менее если у вас есть экземпляр, где не должно применяться правило или профиля, можно легко отключить его непосредственно в коде. Можно использовать `gsl::suppress` атрибут для предотвращения C++ Core Check обнаружения и создания отчетов любое нарушение правила в нем следующий блок кода. Можно пометить отдельные инструкции, чтобы отключить определенные правила. Можно даже отключить весь профиль границы, написав `[[gsl::suppress(bounds)]]` без включения номер конкретного правила.

## <a name="supported-rule-sets"></a>Поддерживаемые наборы правил
Правила проверки C++ Core добавляются новые правила, может увеличить число предупреждений, которые создаются для существующего кода. Заранее заданные наборы правил можно использовать для фильтрации какие типы правил для поддержки.
Справочные разделы для большинства правил находятся под [C++ Core проверьте Справочник по Visual Studio](code-analysis-for-cpp-corecheck.md).

Начиная с Visual Studio 2017 версии 15.3 являются наборы поддерживаемых правил:
- **Правила для указателей владельцев** применять [управления ресурсами проверяет, связанные с owner\<T > из C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Правила для констант** применять [проверки, связанные с const, из C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

- **Правила для необработанных указателей** применять [управления ресурсами проверяет связанные с необработанных указателей, из C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Правила для уникальных указателей** применять [управления ресурсами проверяет, связанные с типами с семантикой уникальных указателей, из C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Правила проверки границ** применять [ограничивающий профиль из C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

- **Правила типов** применять [введите профиля, из C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

**Visual Studio 2017 версии 15.5**:

- **Класс правил** несколько правил, которые фокусируются на правильное использование специальных функций-членов и виртуальных спецификаций. Это подмножество проверок, рекомендуется использовать для [классов и иерархии классов](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class).
- **Правила для параллелизма** одно правило, который перехватывает объекты защиты объявлен неправильно. Дополнительные сведения см. в разделе [рекомендации, связанные с параллелизмом](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency).
- **Правила объявления** несколько правил из [интерфейсы рекомендации](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) какие сосредоточиться на том, как глобальные переменные объявлены.
- **Функция правила** две проверки для помощи при внедрении из `noexcept` спецификатор. Это часть правила [снимите функции проектирования и реализации](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions).
- **Правила для общих указателей** как часть [управления ресурсами](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) в случае принудительного применения рекомендаций мы добавили несколько правил, характерных для указателей как с помощью общих передавались в функции или использовать локально.
- **Правил стиля** один простой, но важных проверки, который эти использование [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Это первый шаг в улучшении кода, стиль и использование выражения и операторы в C++.

**Visual Studio 2017 версии 15.6**:

- **Арифметические правила** правила для определения арифметические [переполнения](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow), [операции со знаком без](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) и [битовые манипуляции](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative).

Вы можете ограничить предупреждения, чтобы только один или несколько групп. **Собственного минимум** и **собственного рекомендуется** правило, включают правила C++ Core Check в дополнение к другим PREfast проверок. Для просмотра доступных наборов правил, откройте диалоговое окно свойств проекта выберите **Analysis\General кода**, откройте раскрывающийся список в **наборы правил** поле со списком и выбора **выбрать несколько наборов правил** . Дополнительные сведения об использовании наборов правил в Visual Studio, см. в разделе [использование наборов правил для группировки правил анализа кода](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Макросы

Правила C++ Core Checker поставляется с файлом заголовка, который определяет макросы, которые упрощают процесс для подавления всей категории предупреждений в коде:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Эти макросы соответствуют наборов правил и разверните узел в список номеров предупреждений с разделителями-пробелами. С помощью конструкций соответствующую директиву pragma, можно настроить эффективный набор правил, интересных для проекта или кода. В следующем примере анализа кода выдает предупреждение, только о отсутствует постоянное модификаторы:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Атрибуты

Компилятор Microsoft Visual C++ имеет ограниченную поддержку для GSL подавлять атрибута. Его можно использовать для подавления предупреждений для выражений и инструкций блока внутри функции.

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppress-analysis-by-using-command-line-options"></a>Отключение анализа при помощи параметров командной строки

Вместо #pragmas Чтобы отключить предупреждения для проекта или отдельного файла можно использовать параметры командной строки на странице свойств файла. Например, чтобы отключить предупреждения 26400 для файла:

1. Щелкните правой кнопкой мыши файл в **обозревателе решений**

2. Выберите **свойства | C / C++ | Командная строка**

3. В **Дополнительные параметры** окна, добавление `/wd26400`.

Можно использовать параметр командной строки будет временно отключить анализатора кода для файла путем указания `/analyze-`. В результате получается предупреждение *D9025 переопределение «/ analyze» с "/ analyze-"*, который напоминает о необходимости снова включить анализ кода в более поздней версии.

## <a name="corecheck_per_file"></a> Включить правила C++ Core Checker для конкретного проекта файлов

Иногда может быть полезно для анализа кода с фокусом ввода и по-прежнему использовать Visual Studio IDE. Следующий пример можно использовать для крупных проектов для экономии времени сборки и было проще отфильтровать результаты:

1. В командной строке задайте `esp.extension` и `esp.annotationbuildlevel` переменные среды.
2. Чтобы наследуют эти переменные, откройте Visual Studio из командной оболочки.
3. Загрузить проект и откройте ее свойства.
4. Включить анализ кода, выбрать наборы соответствующее правило, но не включайте расширения анализа кода.
5. Перейдите к файлу, который вы хотите проанализировать с помощью правила C++ Core Checker и откройте ее свойства.
6. Выберите **C / C++ \Command параметры строки** и добавьте `/analyze:plugin EspXEngine.dll`
7. Отключить использование файла предкомпилированного заголовка (**C / C++ \Precompiled заголовки**). Это необходимо, так как подсистема расширений может попытаться прочитать внутренние сведения из предкомпилированного заголовка (PCH); Если файл PCH скомпилирован с параметрами по умолчанию проекта, он не будут совместимы.
8. Перестройте проект. Распространенные PREFast проверки должны работать на всех файлов. Так как правила C++ Core Checker не включена по умолчанию, он должен выполняться только на файл, который настроен для использования его.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Как использовать правила C++ Core Checker вне Visual Studio

Можно использовать проверки C++ Core Guidelines в автоматических построениях.

### <a name="msbuild"></a>MSBuild
 Средство проверки анализ машинного кода (PREfast) интегрируется в среду MSBuild файлами пользовательских целевых объектов. Можно использовать свойства проекта, чтобы включить его и добавить C++ Core Checker рекомендации (который основан на PREfast):

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Убедитесь, что можно добавить эти свойства перед импортом файла Microsoft.Cpp.targets. Можно выбрать наборы конкретное правило или создать настраиваемый набор правил или использовать набор правил по умолчанию, который включает в себя другие PREfast проверки.

C++ Core Checker можно запустить только на указанные файлы, используя тот же подход, как [описанные ранее](#corecheck_per_file), но с помощью файлов MSBuild. Переменные среды можно задать с помощью `BuildMacro` элемента:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Если вы не хотите изменять файл проекта, свойства можно передать в командной строке:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Проекты, отличных от MSBuild

Если вы используете систему сборки, не зависящая от MSBuild можно запустить средство проверки, но вам нужно ознакомиться с некоторых внутреннее устройство ядра конфигурации анализа кода. Эти внутренние компоненты гарантированно не будет поддерживаться в будущем.

Необходимо задать несколько переменных среды и использовать соответствующие параметры командной строки для компилятора. Лучше работать в среде «Командная строка Native Tools», чтобы у вас нет для поиска для конкретных путей для компилятора, включают каталоги и т. д.

1. **Переменные среды**
   - `set esp.extensions=cppcorecheck.dll` Подсистема для загрузки модуля C++ Core Guidelines.
   - `set esp.annotationbuildlevel=ignore` Это отключает логику, которая обрабатывает заметки SAL. Заметки не влияют на анализ кода в правила C++ Core Checker, но их обработка занимает времени (иногда длинный формат времени). Этот параметр является необязательным, но настоятельно рекомендуется.
   - `set caexcludepath=%include%` Мы настоятельно рекомендуем отключить предупреждения, которые срабатывают на стандартные заголовки. Можно добавить дополнительные пути, например путь к общие заголовки в проекте.
2. **Параметры командной строки**
   - `/analyze`  Включает анализ кода (включая / analyze: только и / analyze: quiet).
   - `/analyze:plugin EspXEngine.dll` Этот параметр, загружает модуль расширения анализа кода в PREfast. Этот модуль, в свою очередь, загружает правила C++ Core Checker.

## <a name="use-the-guideline-support-library"></a>Использование библиотеки поддержки рекомендации
 Библиотека поддержки рекомендация призвана обеспечить следование основных рекомендаций. GSL содержит определения, которые позволяют заменять ошибкам конструкции с более безопасные альтернативы. Например, можно заменить `T*, length` пары параметров с `span<T>` типа. Найти по адресу GSL [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Библиотека является открытым кодом, для просмотра источников, добавлять комментарии или свой вклад. Проект можно найти в [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

## <a name="vs2015_corecheck"></a> Использовать правила C++ Core Check в проектах Visual Studio 2015

Если вы используете Visual Studio 2015, C++ Core Check наборов правил анализа кода не устанавливаются по умолчанию. Необходимо выполнить некоторые дополнительные действия, чтобы можно было включить средства анализа кода C++ Core Check, в Visual Studio 2015. Корпорация Майкрософт предоставляет поддержку для проектов Visual Studio 2015 с помощью пакета Nuget. Пакет называется Microsoft.CppCoreCheck, и оно доступно в [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Этот пакет требует, что у вас есть по крайней мере установлена среда Visual Studio 2015 с обновлением 1.

Пакет также устанавливает другой пакет как зависимость только заголовки рекомендация поддержки библиотеки (GSL). GSL также доступна на сайте GitHub в [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

Из-за того, в который загружаются правил анализа кода необходимо установить пакет Microsoft.CppCoreCheck NuGet в каждый проект C++, который вы хотите проверить в Visual Studio 2015.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Добавление пакета Microsoft.CppCoreCheck в проект в Visual Studio 2015

1. В **обозревателе решений**, щелкните правой кнопкой мыши, чтобы открыть контекстное меню проекта в решении, которое вы хотите добавить пакет. Выберите **управление пакетами NuGet** открыть **диспетчер пакетов NuGet**.

2. В **диспетчер пакетов NuGet** окно, и выполните поиск Microsoft.CppCoreCheck.

    ![Окно диспетчера пакетов NuGet показан пакет CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.png)

3. Выберите пакет Microsoft.CppCoreCheck, а затем выберите **установить** кнопку, чтобы добавить правила в проект.

   Пакет NuGet добавляет дополнительные MSBuild *.targets* файл в проект, который вызывается при включении анализа кода в проекте. Это *.targets* файла добавляет правила C++ Core Check в качестве дополнительного расширения для средства анализа кода в Visual Studio. При установке пакета, можно использовать диалоговое окно страниц свойств для включения или отключения правила выпущенных и экспериментальных.

## <a name="see-also"></a>См. также

- [Справочник по Visual Studio C++ Core Check](code-analysis-for-cpp-corecheck.md)