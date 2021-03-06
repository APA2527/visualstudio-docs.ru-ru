---
title: Как приступить к настройке ленты
description: Узнайте, как настроить ленту Microsoft Office приложения, добавить в проект Office элемент Лента (визуальный конструктор) или лента (XML).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, adding Ribbon to project
- Ribbon [Office development in Visual Studio], adding
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, adding Ribbon to project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3974fe85a97226a920959b41256fa7e29923c9d1
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845951"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Как приступить к настройке ленты
  Чтобы настроить ленту Microsoft Office приложения, добавьте элемент **Лента (визуальный конструктор)** или **Лента (XML)** в проект Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Добавление ленты в проект

1. В меню **проект** выберите команду **Добавить новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите элемент **Лента (визуальный конструктор)** или **Лента (XML)**. Дополнительные сведения об этих шаблонах см. в статье [Общие сведения о ленте](../vsto/ribbon-overview.md).

3. В поле **имя** введите имя элемента ленты.

    Имена не могут содержать следующие символы:

   - Решетка (#)

   - Процент (%)

   - Амперсанд (&)

   - Звездочка (*)

   - Вертикальная черта (|)

   - Обратная косая черта (\\)

   - Двоеточие (:)

   - Двойные кавычки (")

   - Знак "меньше" (\<)

   - Знак «больше» >)

   - Вопросительный знак (?)

   - Косая черта (/)

   - Начальные и конечные пробелы (' ')

   - Имена, зарезервированные для Windows или DOS, такие как ("NUL", "AUX", "Con", "COM1", "LPT1" и т. д.)

4. Нажмите кнопку **ОК**.

   Элемент Лента появится в **Обозреватель решений**. Дополнительные сведения о дальнейших действиях см. в разделе [Лента Overview](../vsto/ribbon-overview.md).

## <a name="see-also"></a>См. также раздел
- [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)
- [Конструктор лент](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Пошаговое руководство. Создание настраиваемой вкладки с помощью XML-ленты](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
