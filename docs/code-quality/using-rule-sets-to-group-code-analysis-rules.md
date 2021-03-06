---
title: Наборы правил анализа кода
ms.date: 04/02/2018
description: Сведения о встроенных и настраиваемых наборах правил в анализе кода Visual Studio. Узнайте, как задавать наборы правил в файлах и как настраивать наборы правил в проектах.
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 980c77067ac237dba13c8c888c358a0adeab6d1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859662"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Использование наборов правил для группировки правил анализа кода

При настройке анализа кода в Visual Studio можно выбрать из списка встроенных *наборов правил*. Набор правил — это группа правил анализа кода, которая определяет целевые проблемы и конкретные условия для этого проекта. Например, можно применить набор правил, предназначенный для просмотра кода для общедоступных интерфейсов API. Можно также применить набор правил, включающий все доступные правила.

Набор правил можно настроить, добавив или удалив правила или изменив серьезность правил, чтобы они отображались как предупреждения или ошибки в **Список ошибок**. Настроенные наборы правил могут удовлетворить потребности конкретной среды разработки. При настройке набора правил редактор набора правил предоставляет средства поиска и фильтрации, помогающие в процессе.

Наборы правил доступны для [анализа управляемого кода](/dotnet/fundamentals/code-analysis/code-quality-rule-options), [традиционного анализа управляемого кода](how-to-configure-code-analysis-for-a-managed-code-project.md)и [анализа кода C++](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run).

## <a name="rule-set-format"></a>Формат набора правил

Набор правил указывается в формате XML в *RuleSet* -файле. Правила, которые состоят из идентификатора и *действия*, группируются по идентификатору анализатора и пространству имен в файле.

Содержимое *RuleSet* -файла выглядит примерно так:

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> Проще [изменить набор правил](../code-quality/working-in-the-code-analysis-rule-set-editor.md) в **редакторе набора правил** , чем вручную.

## <a name="specify-a-rule-set-for-a-project"></a>Укажите набор правил для проекта

Набор правил для проекта указывается свойством **кодеаналисисрулесет** в файле проекта Visual Studio. Пример:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>См. также раздел

- [Справочник по набору правил анализа кода](../code-quality/rule-set-reference.md)