---
title: Свойства дорожек
description: Сведения о том, как дорожки делят диаграмму на вертикальные или горизонтальные области и как можно определить другие фигуры для отображения в дорожках.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 61994a25b5fa862a2014e2dd5b57a0c47130e6ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882990"
---
# <a name="properties-of-swimlanes"></a>Свойства дорожек
На схему можно добавлять дорожки. Дорожки делят диаграмму на вертикальные или горизонтальные области. Можно определить другие фигуры для отображения в дорожках. Дополнительные сведения см. [в разделе Определение языка Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md). Дополнительные сведения об использовании этих свойств см. [в разделе Настройка и расширение языка Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Дорожки имеют свойства, перечисленные в следующей таблице.

|Свойство|Описание|По умолчанию|
|-|-|-|
|Цвет заливки текста|Цвет заливки для текста дорожки.|White|
|Цвет заливки заголовка|Цвет заливки для заголовка дорожки.|даркграй|
|Цвет разделителя|Цвет разделительной линии.|лигхтграй|
|Стиль разделительной линии|Стиль разделительной линии ( `Solid` , `Dash` ,,, `Dot` `DashDot` `DashDotDot` или `Custom` ).|`Dash`|
|Толщина разделителя|Толщина разделительной линии в дюймах.|0,03125|
|Цвет текста|Цвет, используемый для декораторов текста, связанных с этой дорожкой.|Черный|
|Модификатор доступа|Уровень доступа класса ( `public` или `internal` ).|Открытый|
|Настраиваемые атрибуты|Используется для добавления атрибутов к классу кода, созданному из этой дорожки.|\<none>|
|Создает двойное производное|При `True` этом создается как базовый класс, так и разделяемый класс (для поддержки настройки с помощью переопределений). Дополнительные сведения см. [в разделе Переопределение и расширение созданных классов](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Имеет настраиваемый конструктор|Если `True` задано значение, в исходном коде будет указан пользовательский конструктор. Дополнительные сведения см. [в разделе Переопределение и расширение созданных классов](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Модификатор наследования|Описывает тип наследования класса исходного кода, созданного из дорожки ( `none` `abstract` или `sealed` ).|нет|
|Базовая дорожка|Базовый класс этой дорожки.|(нет)|
|Имя|Имя этой дорожки.|Текущее имя|
|Пространство имен|Пространство имен, связанное с этой дорожкой.|Текущее пространство имен|
|Тип подсказки|Определение подсказки ( `fixed` , `variable` или `none` ). При `fixed` значении `Fixed Tooltip Text` используется значение свойства. Если `variable` , то подсказка определяется в пользовательском коде.|\<none>|
|Примечания|Неформальные примечания, связанные с этой дорожкой.|\<none>|
|Выравнивание|Выравнивание по горизонтали или по вертикали.|Vertical|
|Начальная высота|Начальная высота этой дорожки в дюймах. Применяется только к горизонтальным дорожкам.|0|
|Начальная ширина|Начальная ширина этой дорожки в дюймах. Применимо только к вертикальным дорожкам.|0|
|Отображение цвета текста|Если значение `True` равно, пользователь может задать цвет дорожки в созданном конструкторе. Чтобы установить это значение, щелкните правой кнопкой мыши фигуру дорожку и выберите пункт **добавить предоставленный**.|False|
|Описание|Используется для документирования созданного конструктора.|\<none>|
|Отображаемое имя|Имя, которое будет отображаться в созданном конструкторе для ссылки на этот класс дорожки.|\<none>|
|Исправлен текст подсказки|Текст, используемый для фиксированной подсказки.|\<none>|
|Ключевое слово Help|Ключевое слово, используемое для индексации справки F1 для этой дорожки.|\<none>|

## <a name="see-also"></a>См. также раздел

- [Глоссарий средств предметно-ориентированных языков](/previous-versions/bb126564(v=vs.100))