---
title: Свойства определения доменного языка
description: Сведения о том, что свойства DslDefinition определяют свойства определения доменного языка, такие как нумерация версий.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48771a61577c5c7ca910cc3b4f8496db37ada281
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360524"
---
# <a name="properties-of-a-dsl-definition"></a>Свойства определения доменного языка
Свойства DslDefinition определяют свойства определения *доменного языка* , такие как нумерация версий. Свойства DslDefinition отображаются в окне **Свойства** при щелчке открытой области диаграммы в *конструктор предметно-ориентированных языков*.

 Дополнительные сведения см. [в разделе Определение языка Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md). Дополнительные сведения об использовании этих свойств см. [в разделе Настройка и расширение языка Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition имеет свойства, приведенные в следующей таблице:

|Свойство|Описание|Значение по умолчанию|
|-|-|-|
|Модификатор доступа|Определяет, является ли модификатор доступа для класса домена открытым или внутренними.|public|
|Настраиваемые атрибуты|Пользовательские определенные атрибуты для доменного класса.<br /><br /> **Примечание** . Используйте кнопку Обзор, чтобы добавить атрибут.|\<none>|
|Название организации|Имя текущего названия компании в системном реестре.|Название текущей компании|
|Имя|Имя этого доменного класса.|Текущее имя|
|Пространство имен|Пространство имен, связанное с этим доменным классом.|Текущее пространство имен|
|Идентификатор GUID пакета|GUID для пакета Visual Studio, созданного для этого языка DSL.|\<none>|
|Пространство имен пакета|Пространство имен для пакета Visual Studio, созданного для этого языка DSL.|\<none>|
|Название продукта|Имя продукта, которое будет зарегистрировано для пакета Visual Studio, созданного для этого языка DSL.|\<none>|
|Примечания|Примечания, связанные с этим классом домена.|\<none>|
|Описание|Описание для этого доменного класса.|\<none>|
|Отображаемое имя|Имя, которое будет отображаться в созданном конструкторе для этого доменного класса.|\<none>|
|Ключевое слово Help|Ключевое слово справки, связанное с этим классом домена.|\<none>|
|Сборка|Номер добавочной сборки для этого определения доменного языка.|0|
|Основная версия|Добавочный номер основной сборки для этого определения доменного языка.|1|
|Вспомогательная версия|Добавочный дополнительный номер сборки для этого определения доменного языка.|0|
|Редакция|Номер сборки добавочной редакции для данного определения доменного языка.|0|

## <a name="see-also"></a>См. также раздел

- [Глоссарий средств предметно-ориентированных языков](/previous-versions/bb126564(v=vs.100))