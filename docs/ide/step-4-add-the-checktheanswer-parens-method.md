---
title: Шаг 4. Добавление метода CheckTheAnswer()
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c691b1db57fa1a00ad33441e36ff0f7f79716f11
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416512"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Шаг 4. Добавление метода CheckTheAnswer()
В четвертой части этого урока вам предстоит написать метод `CheckTheAnswer()`, который проверяет правильность ответов на арифметические задачи. Этот раздел входит в серию учебников, посвященных основам написания кода. Общие сведения об учебнике см. в разделе [Руководство 2. Создание ограниченной по времени математической головоломки](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Если вы разрабатываете головоломку на Visual Basic, вам необходимо будет использовать ключевое слово `Function` вместо обычного ключевого слова `Sub`, потому что этот метод возвращает значение. Это объясняется просто: процедуры не возвращают значения, в отличие от функций.

## <a name="to-verify-whether-the-answers-are-correct"></a>Проверка правильности ответов

1. Добавьте метод `CheckTheAnswer()`.

     При вызове этот метод складывает значения addend1 и addend2, а затем сравнивает результат со значением в элементе управления <xref:System.Windows.Forms.NumericUpDown> с именем sum. Если значения равны, метод возвращает значение `true`. В противном случае метод возвращает значение `false`. Код должен выглядеть так, как показано ниже.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     Далее предстоит проверить ответ путем изменения кода в этом методе, чтобы обработчик события <xref:System.Windows.Forms.Timer.Tick> таймера вызвал новый метод `CheckTheAnswer()`.

2. Добавьте следующий код в оператор `if else`.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Если ответ правильный, `CheckTheAnswer()` возвращает значение `true`. Обработчик событий останавливает таймер, выводит поздравительное сообщение, а затем снова делает кнопку **Запуск** доступной. В противном случае головоломка продолжается.

3. Сохраните программу, запустите ее, запустите головоломку и введите правильный ответ на задачу сложения.

    > [!NOTE]
    > При вводе ответа необходимо либо выделить значение по умолчанию перед началом ввода ответа, либо удалить нуль вручную. Позднее в этом уроке мы исправим это поведение.

     При вводе правильного ответа появляется окно сообщения, кнопка **Запуск** становится доступной, и таймер останавливается.

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий раздел руководства: [Шаг 5. Добавление обработчиков событий входа для элементов управления NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).

- Предыдущий раздел руководства: [Шаг 3. Добавление таймера с обратным отсчетом](../ide/step-3-add-a-countdown-timer.md).
