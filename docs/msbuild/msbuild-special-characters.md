---
title: Специальные знаки MSBuild | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a87013ff3a1911caa667f7ba431e408fc87a98f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004636"
---
# <a name="msbuild-special-characters"></a>Специальные символы в MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] резервирует некоторые знаки для специального применения в определенных контекстах. Эти знаки следует экранировать, только если вы хотите использовать их именно в том контексте, для которого они зарезервированы. Например, звездочка имеет специальное значение только в атрибутах `Include` и `Exclude` определения элемента, а также в вызовах `CreateItem`. Если требуется, чтобы звездочка отображалась как звездочка в одном из этих контекстов, нужно экранировать ее. В любом другом контексте просто введите звездочку там, где она нужна.

 Чтобы экранировать специальный символ, используйте синтаксис %\<xx>, где \<xx> представляет шестнадцатеричное ASCII-значение знака. Дополнительные сведения см. в разделе [Как Пропуск специальных знаков в MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Специальные символы
 В следующей таблице перечислены специальные знаки [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]:

|**Знак**|**ASCII**|**Зарезервированное использование**|
|-------------------|---------------|------------------------|
|%|%25|Ссылки на метаданные|
|$|%24|Ссылки на свойства|
|@|%40|Списки элементов|
|\'|%27|Условия и другие выражения|
|;|%3B|Разделитель элементов списка|
|?|%3F|Подстановочный знак для имен файлов в атрибутах `Include` и `Exclude`|
|*|%2A|Подстановочный знак для использования в именах файлов в атрибутах `Include` и `Exclude`|

## <a name="see-also"></a>См. также
- [Дополнительные возможности](../msbuild/msbuild-advanced-concepts.md)
- [Элементы](../msbuild/msbuild-items.md)