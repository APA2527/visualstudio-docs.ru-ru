---
title: XML-фрагменты
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f2bcdd0c28d7b4b99c92d3346b32ed34aa92a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592325"
---
# <a name="xml-snippets"></a>XML-фрагменты

В редакторе XML доступна возможность, называемая *XML-фрагментами*, которая позволяет более быстро создавать XML-файлы. XML-фрагменты можно использовать повторно, вставляя их в файлы. Также можно создавать XML-данные, исходя из схемы на языке XSD.

## <a name="reusable-xml-snippets"></a>Повторно используемые XML-фрагменты

В редакторе XML содержится множество фрагментов, охватывающих некоторые распространенные задачи. Это позволяет более легко создавать XML-файлы. Например, при создании или редактировании XML-схемы с помощью фрагментов "Элемент последовательности сложного типа" и "Элемент простого типа" в файл вставляется следующий текст XML. Затем при необходимости можно изменить значение `name`.

```xml
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

Существует два способа вставки фрагментов. Команда **Вставить фрагмент кода** вставляет XML-фрагмент в положении курсора. Команда **Разместить во фрагменте** заключает выделенный текст в XML-фрагмент. Обе команды доступны из вложенного меню **IntelliSense** в меню **Правка** либо из контекстного меню редактора.

Дополнительные сведения см. в разделе [Практическое руководство. Использование фрагментов XML](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>XML-фрагменты, сформированные схемой

В редакторе XML также можно создавать XML-фрагменты на основе XML-схем. Эта функция позволяет заполнять элементы XML-элементами, созданными из информации схемы для этого элемента. Дополнительные сведения см. в разделе [Практическое руководство. Создание фрагмента XML из схемы XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)

## <a name="create-new-xml-snippets"></a>Создание XML-фрагментов

Кроме фрагментов, по умолчанию входящих в Visual Studio, можно также создавать собственные XML-фрагменты. Дополнительные сведения см. в разделе [Практическое руководство. Создание XML-фрагментов](../xml-tools/how-to-create-xml-snippets.md)

## <a name="see-also"></a>См. также

- [Фрагменты кода в Visual Studio](../ide/code-snippets.md)
- [Редактор XML](../xml-tools/xml-editor.md)
