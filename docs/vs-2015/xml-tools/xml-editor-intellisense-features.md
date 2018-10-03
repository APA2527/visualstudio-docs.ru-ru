---
title: Возможности IntelliSense редактора XML | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 983410eec11799fb05ad66e13df1aea95be8e8f3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559642"
---
# <a name="xml-editor-intellisense-features"></a>Возможности IntelliSense редактора XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [возможности IntelliSense редактора XML](https://docs.microsoft.com/visualstudio/xml-tools/xml-editor-intellisense-features).  
  
  
Редактор XML предоставляет полные возможности IntelliSense, сравнимые с другими языковыми редакторами в Visual Studio. Данный раздел поясняет использование IntelliSense с языком определения схемы XML (XSD) и документами XSLT.  
  
## <a name="intellisense-in-an-xsd-document"></a>IntelliSense в документе XSD  
 После того как схема связана с документом, вы увидите список ожидаемых элементов раскрывающегося списка каждый раз при вводе `"<"` или нажмите кнопку **отображать список членов объекта** кнопки на панели инструментов редактора XML. Сведения о связывании схем с XML-документов, см. в разделе [Проверка XML-документа](../xml-tools/xml-document-validation.md).  
  
 После ввода пробела внутри открывающего тега также раскрывается список всех атрибутов, которые можно добавить к текущему элементу.  
  
 После ввода знака `"="` для указания значения атрибута (или, для той же цели, открывающей кавычки) также появляется список возможных значений этого атрибута. Значения предоставляются только в том случае, если схема содержит перечисленные значения в аспектах `xsd:enumeration` или если атрибут имеет тип `Boolean`. Средствами IntelliSense предоставляется также список известных кодов языков для значения `xml:lang` или любого типа `simpleType`, производного от `xsd:language`. Для деклараций пространств имен выводится предусмотренный средствами IntelliSense список известных значений `targetNamespace`.  
  
 Список IntelliSense известных значений также предоставляется после ввода знака `">"` для закрытия открывающего тега, если элемент имеет тип `simpleType`. Действия с элементами аналогичны действиям с атрибутами, описанным в предыдущем абзаце.  
  
 Кроме того, в этих списках IntelliSense выводятся также подсказки на основе данных `xsd:annotation` и `xsd:documentation`, находящихся в связанной схеме.  
  
## <a name="intellisense-in-an-xslt-document"></a>IntelliSense в документе XSLT  
 После добавления именованного шаблона или атрибута в документ XSLT можно использовать IntelliSense для вставки следующего:  
  
-   имен наборов атрибутов,  
  
-   режимов шаблона,  
  
-   имен шаблона,  
  
-   имен параметров для данного режима,  
  
-   имен параметров для данного именованного шаблона.  
  
 Дополнительные сведения см. в разделе [Пошаговое руководство: использование XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md) раздела.  
  
## <a name="auto-completion"></a>Автоматическое завершение  
 Редактор XML облегчает также редактирование XML-документов, автоматически вставляя необходимые элементы синтаксиса. Например, если ввести следующий открывающий тег:  
  
 `<book>`  
  
 Редактор добавляет закрывающий тег и помещает курсор после открывающего тега. Ниже приведен пример этого («&#124;» указывает положение курсора):  
  
 `<book>`&#124;`</book>`  
  
 Поскольку значения атрибутов должны быть всегда заключены в кавычки, редактор XML автоматически вставляет кавычки. Например, если ввести следующий текст:  
  
 `<book title=`  
  
 Редактор XML вставляет кавычки и помещает курсор между ними:  
  
 `<book title="`&#124;`"`  
  
 Аналогичным образом, редактор XML автоматически вставляет следующие элементы синтаксиса:  
  
-   Окончание инструкции по обработке:`?>`  
  
-   Окончание блока CDATA:`]]>`  
  
-   Окончание комментария:`-->`  
  
-   Окончание DTD-декларации:`>`  
  
 XML Editor также может вставить декларацию пространств имен, если выбран уточненный обозначением пространства имен элемент или атрибут из списка IntelliSense, при том что пространство имен для этого элемента или атрибута еще не находится в области видимости.  
  
 Например, если выбрать элемент `e:Book` из списка IntelliSense, где префикс привязан к пространству имен `http://books`, еще не объявленному в документе, редактор XML вставит необходимую декларацию пространства имен. Ниже показан результирующий XML-текст.  
  
 `<e:Book xmlns:e="http://books"`  
  
## <a name="brace-matching"></a>Согласование скобок  
 Редактор XML выделяет скобки подсветкой, что позволяет проверять формат элементов сразу после их закрытия. Можно также с помощью сочетания клавиш CTRL+] переходить от одной парной скобки к другой.  
  
 Редактор XML выполняет это действие для следующих элементов.  
  
-   Согласованные открывающий и закрывающий теги.  
  
-   Любая пара "\<" или «>» угловые скобки.  
  
-   Начало и конец комментария.  
  
-   Начало и конец инструкций по обработке.  
  
-   Начало и конец блока CDATA.  
  
-   Начало и конец DTD-деклараций.  
  
-   Открывающие и закрывающие кавычки атрибутов.  
  
## <a name="modifying-the-intellisense-options"></a>Изменение параметров IntelliSense  
 Функции IntelliSense и автоматического завершения по умолчанию включены. Однако их можно выключить, изменив настройки «Сервис» и «Параметры».  
  
 **Автоматическая вставка** раздел **Разное** страницы управляет следующими действиями:  
  
|name|Описание|  
|----------|-----------------|  
|Закрывать теги|Вставляет закрывающие теги для новых элементов.|  
|Кавычки для атрибутов|Вставляет кавычки для значений атрибутов при вводе имени нового атрибута.|  
|Прочая разметка|Завершает комментарии, CDATA, DOCTYPE, инструкции обработки и другие декларации разметки.|  
  
#### <a name="to-change-the-auto-completion-behavior"></a>Изменение поведения функции автоматического завершения  
  
1.  В меню **Сервис** выберите пункт **Параметры**.  
  
2.  Разверните **текстовый редактор**, разверните **XML**и выберите **Разное**.  
  
3.  Внесите изменения в **автоматическая вставка** раздела и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Редактор XML](../xml-tools/xml-editor.md)   
 [Использование IntelliSense](../ide/using-intellisense.md)   
 [Пошаговое руководство. Использование XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md)


