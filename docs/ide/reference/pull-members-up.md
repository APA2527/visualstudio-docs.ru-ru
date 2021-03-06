---
title: Подъем элементов
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для подъема элементов до базового типа.
ms.custom: SEO-VS-2020
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 159608644cb641aa2c84e4d55e92156215069030
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616880"
---
# <a name="pull-members-up"></a>Подъем элементов

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Позволяет поднимать элементы до базового типа.

**Когда?** Вы реализовали интерфейс и хотите переместить элемент в базовый тип.

**Зачем?** Подъем членов позволяет другим реализациям вашего интерфейса также наследовать эти элементы.

## <a name="how-to"></a>Практические советы

1. Поместите курсор в любом элементе реализованного интерфейса.
2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

   ![Подъем элементов](media/pull-members-up.png)

2. Выберите **Подъем элементов до базового типа**.

3. В диалоговом окне выберите, какие элементы вы хотите добавить к выбранному интерфейсу.

   ![Подъем элемента](media/pull-members-up-dialog.png)

4. Нажмите кнопку **ОК**. Выбранные элементы поднимаются к интерфейсу.

   ![Подъем элемента завершен](media/pull-members-up-completed.png)

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)
