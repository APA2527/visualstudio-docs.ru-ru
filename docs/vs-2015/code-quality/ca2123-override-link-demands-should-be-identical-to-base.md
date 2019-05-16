---
title: CA2123. Компоновки переопределения должны быть идентичны базовым | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 338d61db9c24972b7fef656498abd43f8ea0b976
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687224"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123. Переопределяющие требования ссылки должны быть идентичны базовым
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод в открытом типе переопределяет метод или реализует интерфейс и не имеют одинаковые [требования связывания](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) как интерфейс или виртуальный метод.

## <a name="rule-description"></a>Описание правила
 Это правило сравнивает метод с его базовым методом (который является интерфейсом или виртуальным методом другого типа), а затем сравнивает запросы ссылок для каждого из них. Нарушение отмечается в том случае, если метод или метод базового содержит запрос компоновки, а другой — нет.

 Если это правило нарушается, злонамеренный вызывающий объект может обойти запрос ссылок путем вызова небезопасного метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, примените то же требование ссылки к переопределению метода или реализации. Если это невозможно, пометьте метод полное требование или полностью удалить атрибут.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Следующий пример показывает различные нарушения этого правила.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.OverridesAndSecurity/cs/FxCop.Security.OverridesAndSecurity.cs#1)]

## <a name="see-also"></a>См. также
 [Правила написания безопасного кода](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [требования связывания](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
