---
title: Преобразование запроса LINQ в оператор foreach
ms.custom: SEO-VS-2020
description: Выполните рефакторинг кода для преобразования любого запроса LINQ, написанного с использованием синтаксиса запросов, в оператор foreach.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 832c4160d743ca35dbe41eb0f0cbafd81d60dd26
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102561"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Рефакторинг кода для преобразования запроса LINQ в оператор foreach

Этот рефакторинг кода позволяет преобразовать [синтаксис запроса LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) в оператор [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Область применения этого рефакторинга:

- C#

- Visual Basic

## <a name="how-to-use-it"></a>Использование

1. Выберите весь запрос LINQ начиная с `from`.

   > [!NOTE]
   > Этот рефакторинг кода позволяет преобразовывать только запросы LINQ, выраженные с помощью синтаксиса запроса, а не синтаксиса метода.

1. Нажмите клавиши **CTRL**+ **.** или щелкните значок отвертки ![значок отвертки](../media/screwdriver-icon.png) на полях файла кода.

   ![Преобразование запроса LINQ в foreach через меню быстрых действий](media/convert-linq-to-foreach.png)

1. Выберите **Преобразовать в foreach**. Также можно выбрать **Просмотр изменений** , чтобы открыть диалоговое окно [Просмотр изменений](../../ide/preview-changes.md), и нажать **Применить**.

> [!NOTE]
> Код C#, созданный в процессе выполнения рефакторинга, использует явный тип или ключевое слово [var](/dotnet/csharp/language-reference/keywords/var) для переменной итерации цикла `foreach`. Тип в созданном коде (явный или неявный) зависит от параметров стиля кода, которые находятся в области. Эти конкретные параметры стиля кода задаются на уровне компьютера в разделе **Сервис** > **Параметры** > **Текстовый редактор** > **C#**  > **Стиль кода** > **Общие** >  **\'предпочтения "var"** или на уровне решения в файле [EditorConfig](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types). Если вы измените эти параметры в меню **Параметры** , снова откройте файл кода, чтобы изменения вступили в силу.

## <a name="see-also"></a>См. также раздел

- [LINQ](/dotnet/standard/using-linq)
- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)
