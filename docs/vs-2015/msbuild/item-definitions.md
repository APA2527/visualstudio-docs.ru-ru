---
title: Определения элементов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7097311c3d1aae718096c3bf74ec04c3e5ea8818
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433592"
---
# <a name="item-definitions"></a>Определения элементов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0 поддерживается статическое объявление элементов в файлах проекта с использованием элемента [ItemGroup](../msbuild/itemgroup-element-msbuild.md). Однако метаданные можно добавлять только на уровне элемента, даже если метаданные для всех элементов идентичны. Начиная с версии [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5 элемент проекта с именем [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) позволяет обойти это ограничение. *ItemDefinitionGroup* позволяет определить набор определений элементов, который добавляет значения метаданных по умолчанию для всех элементов в именованном типе элементов.  
  
 Элемент *ItemDefinitionGroup* располагается непосредственно за элементом [Project](../msbuild/project-element-msbuild.md) в файле проекта. Определения элементов предоставляют следующие функциональные возможности:  
  
- Вы можете определить глобальные метаданные по умолчанию для элементов вне целевого объекта. То есть одни и те же метаданные применяются ко всем элементам заданного типа.  
  
- У типов элементов может быть несколько определений. При добавлении к типу дополнительных спецификаций метаданных приоритет получает последняя из них. \(Порядок импорта метаданных совпадает с порядком импорта свойств.\)  
  
- Метаданные могут быть аддитивными. Например, при определенных условиях значения CDefines накапливаются в зависимости от заданных свойств. Например, `MT;STD_CALL;DEBUG;UNICODE`.  
  
- Метаданные могут быть удалены.  
  
- Для управления включением метаданных можно использовать условия.  
  
## <a name="item-metadata-default-values"></a>Значения метаданных элементов по умолчанию  
 Метаданные элементов, определяемые в ItemDefinitionGroup, являются объявлением метаданных по умолчанию. Метаданные не применяются, если не определен элемент, использующий ItemGroup для хранения значений метаданных.  
  
> [!NOTE]
> Во многих примерах в этом разделе показан элемент ItemDefinitionGroup, но соответствующее определение ItemGroup опущено для ясности.  
  
 Метаданные, явно определенные в ItemGroup, имеют приоритет над метаданными в ItemDefinitionGroup. Метаданные в ItemDefinitionGroup применяются только для метаданных, не определенных в ItemGroup. Например:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>        
</ItemDefinitionGroup>  
<ItemGroup>  
    <i Include="a">  
        <o>o1</o>  
        <n>n2</n>  
    </i>  
</ItemGroup>  
```  
  
 В этом примере к элементу i применяются метаданные по умолчанию m, так как метаданные m не определены явным образом элементом i. Однако к элементу i не применяются метаданные по умолчанию n, так как метаданные n уже определены элементом i.  
  
> [!NOTE]
> В именах элементов и параметров XML учитывается регистр. В именах метаданных элементов и \/свойств элемента регистр не учитывается. Поэтому имена элементов ItemDefinitionGroup, отличающиеся только регистром, следует рассматривать как одинаковые элементы ItemGroup.  
  
## <a name="value-sources"></a>Источники значений  
 Значения для метаданных, определенных в ItemDefinitionGroup, могут поступать из множества различных источников:  
  
- свойство PropertyGroup;  
  
- элемент из ItemDefinitionGroup;  
  
- преобразование элемента в элементе ItemDefinitionGroup;  
  
- переменная среды;  
  
- глобальное свойство \(из командной строки MSBuild.exe\);  
  
- зарезервированное свойство;  
  
- стандартные метаданные в элементе из ItemDefinitionGroup;  
  
- раздел CDATA \<\!\[CDATA\[содержимое не анализируется\]\]\>.  
  
> [!NOTE]
> Метаданные элементов из ItemGroup не используются при объявлении метаданных ItemDefinitionGroup, так как элементы ItemDefinitionGroup обрабатываются раньше элементов ItemGroup.  
  
## <a name="additive-and-multiple-definitions"></a>Аддитивные и множественные определения  
 При добавлении определений или использовании нескольких элементов ItemDefinitionGroups учитывайте следующее:  
  
- Дополнительные спецификации метаданных добавляются к типу.  
  
- Последняя спецификация имеет приоритет.  
  
  Если имеется несколько элементов ItemDefinitionGroups, каждая следующая спецификация добавляет метаданные в предыдущее определение. Например:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <o>o1</o>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 В этом примере метаданные o добавляются к m и n.  
  
 Кроме того, могут быть также добавлены ранее определенные значения метаданных. Например:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
 В этом примере ранее определенное значение для метаданных m \(m1\) добавляется к новому значению \(m2\), в результате чего конечное значение будет m1; m2.  
  
> [!NOTE]
> Это также может выполняться в одной группе ItemDefinitionGroup.  
  
 При переопределении ранее определенных метаданных приоритет получает последняя спецификация. В следующем примере конечное значение метаданных m меняется со значения m1 на m1a.  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>m1a</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
## <a name="using-conditions-in-an-itemdefinitiongroup"></a>Использование условий в ItemDefinitionGroup  
 Для управления включением метаданных можно использовать условия в ItemDefinitionGroup. Например:  
  
```  
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 В этом примере в элемент i включаются метаданные по умолчанию m1, только если значение свойства Configuration имеет значение Debug.  
  
> [!NOTE]
> В условиях поддерживаются только локальные ссылки на метаданные.  
  
 Ссылки на метаданные, ранее определенные в ItemDefinitionGroup, являются локальными для элемента, а не для группы определений. То есть область действия ссылок определяется элементом. Например:  
  
```  
<ItemDefinitionGroup>  
    <test>  
        <yes>1</yes>  
    </test>  
    <i>  
        <m Condition="'%(test.yes)'=='1'">m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 В этом примере элемент "i" содержит ссылку на элемент "test" в условии Condition.  
  
## <a name="overriding-and-deleting-metadata"></a>Переопределение и удаление метаданных  
 Метаданные, определенные в элементе ItemDefinitionGroup, можно переопределить в последующем элементе ItemDefinitionGroup, присвоив им пустое значение. Кроме того, можно удалить элемент метаданных, задав для него пустое значение. Например:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m></m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Элемент i все равно содержит метаданные m, но его значение теперь пустое.  
  
## <a name="scope-of-metadata"></a>Область действия метаданных  
 Элементы ItemDefinitionGroups имеют глобальную область действия на заданные и глобальные свойства, независимо от того, где они определены. Определения метаданных по умолчанию в ItemDefinitionGroup могут ссылаться сами на себя. Например, в следующем примере используется простая ссылка на метаданные:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Кроме того, можно использовать полную ссылку на метаданные:  
  
```  
<ItemDefinitionGroup>  
    <i>  
      <m>m1</m>  
      <m>%(i.m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Однако следующая ссылка недопустима:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>@(x)</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Начиная с версии [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5 ItemGroups также могут ссылаться сами на себя. Например:  
  
```  
<ItemGroup>  
    <item Include="a">  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </item>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Пакетная обработка в MSBuild](../msbuild/msbuild-batching.md)
