---
title: Изменение имени файла в соответствии с типом
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для переименования типа в соответствии с именем файла или переименования файла в соответствии с типом, который он содержит.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: c02135074ee4a4907bb9c4ee235655fc3908a64c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838600"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Рефакторинг для синхронизации типа с именем файла или имени файла с типом

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Вы можете переименовать тип в соответствии с именем файла или изменить имя файла в соответствии с типом, который он содержит.

**Когда?** Вы переименовали файл или тип и еще не обновили их в соответствии с их именами.

**Зачем?** Если поместить тип в файл с другим именем (или наоборот), вам трудно будет найти нужный файл или тип. Если переименовать тип или файл, будет проще читать код и удобнее переходить по нему.

> [!NOTE]
> Этот рефакторинг пока недоступен для проектов .NET Standard и .NET Core.

## <a name="how-to"></a>Практическое руководство

1. Выделите имя типа, который требуется синхронизировать, или поместите в него текстовый курсор.

   - C#:

       ![Выделенный код — C#](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![Выделенный код — Visual Basic](media/synctype-highlight-vb.png)

2. Затем выполните одно из следующих действий.

   - **Клавиатура**
      - Нажмите клавиши **CTRL**+ **.** чтобы активировать меню **Быстрые действия и рефакторинг**. Затем во всплывающем окне предварительного просмотра выберите пункт **Переименовать файл в *имя_типа*.cs**, где *имя_типа* — это имя выбранного вами типа.
      - Нажмите клавиши **CTRL**+ **.** чтобы активировать меню **Быстрые действия и рефакторинг**. Затем во всплывающем окне предварительного просмотра выберите пункт **Переименовать тип в _Имя файла_**, где *Имя файла* — это имя текущего файла.
   - **Мышь**
      - Щелкните код правой кнопкой мыши и выберите меню **Быстрые действия и рефакторинг**. Затем во всплывающем окне предварительного просмотра выберите пункт **Переименовать файл в *имя_типа*.cs**, где *имя_типа* — это имя выбранного вами типа.
      - Щелкните код правой кнопкой мыши и выберите меню **Быстрые действия и рефакторинг**. Затем во всплывающем окне предварительного просмотра выберите пункт **Переименовать тип в _Имя файла_**, где *имя файла* — это имя выбранного вами файла.

   Тип или файл переименован.

   - C#: в примере ниже файл **MyClass.cs** переименован в **MyNewClass.cs**, чтобы его имя совпадало с именем типа.

       ![Встроенный результат — C#](media/synctype-result-cs.png)

   - Visual Basic: в примере ниже файл **Employee.cs** был переименован в **Person.cs**, чтобы его имя совпадало с именем типа.

       ![Встроенный результат — Visual Basic](media/synctype-result-vb.png)

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)
