---
title: Добавление узлов в рабочую область из обозревателя схемы XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2049b8da1caa4e0af0afc52aec6e75f499d85b8b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592819"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Практическое руководство. Добавление узлов в рабочую область в обозревателе схем XML

В этом разделе описывается процесс добавления узлов в [рабочую область конструктора схемы XML](../xml-tools/xml-schema-designer-workspace.md) в **обозревателе схемы XML**. Цель может быть достигнута посредством перетаскивания узлов из **обозревателя схемы XML** в представление конструктора XSD или с использованием контекстного меню **обозревателя схемы XML**. Можно также добавить узлы, выделенные в результате поиска, выполненного в **обозревателе XML-схем**. Дополнительные сведения см. в разделе [Практическое руководство. Добавление в рабочую область узлов, полученных в результате поиска набора схем](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> В [рабочую область конструктора схемы XML](../xml-tools/xml-schema-designer-workspace.md) можно добавлять только глобальные узлы.

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Добавление узлов посредством контекстного меню обозревателя XML

1. Выполните действия, описанные в статье [Практическое руководство. Создание и изменение файла схемы XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. В обозревателе XSD щелкните правой кнопкой мыши узел `PurchaseOrderType`. Выберите **Показать в представлении графика**.

     Узел `purchaseOrderType` будет отображен в области конструктора в представлении графиков.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Перетаскивание узла на представление

1. В представлении графика щелкните правой кнопкой мыши узел `PurchaseOrderType`. Выберите **Показать в обозревателе схемы XML**.

     Узел будет выделен в **обозревателе схемы XML**.

2. Щелкните правой кнопкой мыши узел `PurchaseOrderType` в **обозревателе схемы XML** и выберите **Показать все ссылки**.

     Узел `purchaseOrder` выделен.

3. Перетащите узел `purchaseOrder` в представление графика.

     Узел `purchaseOrder` и узел `PurchaseOrderType` будут отображены рядом друг с другом в области конструктора в представлении графиков. Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Добавление узлов с использованием возможностей поиска обозревателя схем

1. Введите purchaseOrder в текстовом поле поиска панели инструментов [обозревателя схемы XML](../xml-tools/xml-schema-explorer.md) и нажмите кнопку поиска.

     ![Поиск по ключевым словам в обозревателе схемы XML](../xml-tools/media/schemaexplorersearch.gif)

     Результаты поиска также выделяются в **обозревателе схемы XML** и отмечаются галочками на вертикальной полосе прокрутки.

2. Добавьте результаты поиска в рабочую область, нажав кнопку **Добавить выделенные узлы в рабочую область** на панели сводных результатов.

     ![Результат поиска в обозревателе схемы XML](../xml-tools/media/schemaexplorersearchresult.gif)

     Узлы `purchaseOrder` и `PurchaseOrderType` будут отображены рядом друг с другом в области конструктора в [представлении графика](../xml-tools/graph-view.md). Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.

## <a name="see-also"></a>См. также

- [Обозреватель схемы XML](../xml-tools/xml-schema-explorer.md)
