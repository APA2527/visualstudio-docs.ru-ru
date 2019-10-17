---
title: Шаг 8. Добавление метода для проверки того, выиграл ли игрок
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eed7a2796f08e85441c174e882c00fa406cb2379
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289658"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Шаг 8. Добавление метода для проверки того, выиграл ли игрок
Вы создали интересную игру, но требуется еще один элемент, чтобы завершить ее. Игра должна заканчиваться победой игрока, поэтому необходимо добавить метод `CheckForWinner()` для проверки, выиграл ли игрок.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Добавление метода для проверки, выиграл ли игрок

1. Добавьте метод `CheckForWinner()` в нижнюю часть кода, под обработчиком событий `timer1_Tick()`, как показано в следующем коде.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

      > [!IMPORTANT]
      > Используйте элемент управления языка программирования в правом верхнем углу этой страницы, чтобы просмотреть фрагмент кода на C# или Visual Basic.<br><br>![Элемент управления языка программирования для Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)     

     В этом методе используется еще один цикл `foreach` для C# или цикл `For Each` для Visual Basic, чтобы пройти по каждой метке в <xref:System.Windows.Forms.TableLayoutPanel>. Он использует оператор равенства (`==` в Visual C# и `=` в Visual Basic) для проверки цвета значка каждой метки на соответствие цвету фона. Если цвета совпадают, значок остается невидимым, а значит игрок не подобрал пару оставшимся значкам. В этом случае программа использует оператор `return`, чтобы пропустить оставшуюся часть метода. Если цикл прошел через все метки без выполнения оператора `return`, значит, всем значкам в форме была подобрана пара. Программа отображает окно MessageBox с поздравлением победителя, а затем вызывает метод формы `Close()` для завершения игры.

2. После этого обработчик событий <xref:System.Windows.Forms.Control.Click> метки вызывает новый метод `CheckForWinner()`. Убедитесь, что программа проверяет наличие победителя сразу после отображения второго значка, который выбирает игрок. Найдите строку, где задается цвет второму значку, который вы выбрали, и после этой операции вызовите метод `CheckForWinner()`, как показано в следующем коде.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3. Сохраните и выполните программу. Сыграйте в игру и подберите пару всем значкам. Если вы победили, программа отображает сообщение **MessageBox** с поздравлением (как показано на следующем рисунке) и закрывает окно.

     ![Игра "Подбери пару!" с MessageBox](../ide/media/express_tut4step8.png)<br/>
**Игра "Подбери пару!"** с **MessageBox**

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий раздел руководства: [Шаг 9. Изучение других возможностей](../ide/step-9-try-other-features.md).

- Предыдущий раздел руководства: [Шаг 7. Отмена исчезновения пар значков](../ide/step-7-keep-pairs-visible.md).
