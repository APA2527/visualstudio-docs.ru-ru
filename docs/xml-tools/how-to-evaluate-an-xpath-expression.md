---
title: Вычисление выражения XPath при отладке
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64113461cd081eb97e2eb927119f1cd67f8a8d6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816258"
---
# <a name="evaluate-xpath-expressions"></a>Вычисление выражений XPath

Выражения XPath можно вычислить с помощью окна **Быстрая проверка** во время отладки. Выражение XPath должно быть допустимым и соответствовать рекомендация W3C языка XPath версии 1.0. Текущий XSLT-контекст (то есть узел `self::node()` в окне **Локальные значения**) — это контекст вычисления выражения XPath.

При вычислении выражения XPath:

- Поддерживаются встроенные функции XPath.

- Не поддерживаются встроенные функции XSLT и пользовательские функции.

> [!NOTE]
> Отладка XSLT предоставляется только в выпуске Visual Studio 2017 Enterprise.

## <a name="evaluate-an-xpath-expression"></a>Вычисление выражения XPath

В следующей процедуре используются файлы *below-average.xsl* и *books.xml* из статьи [Пошаговое руководство. Отладка таблицы стилей XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files).

1. Добавьте точку останова в начальный тег `xsl:if`.

2. Чтобы начать отладку, в строке меню выберите **XML** > **Начать отладку XSLT** (или нажмите **ALT**+**F5**).

   Отладчик начинается и останавлявается на теге `xsl:if`.

3. Щелкните правой кнопкой мыши и выберите пункт **Быстрая проверка**.

   Откроется окно **Быстрая проверка**.

4. Введите `./price/text()` в поле **Выражение** в диалоговом окне **Быстрая проверка** и нажмите кнопку **Пересчитать**.

   В поле **Значение** появится цена для текущего узла книги.

   ![Вычисление выражения XPath в окне "Быстрая проверка"](media/quickwatch-price.png)

5. Измените выражение XPath на `./price/text() < $bookAverage` и нажмите кнопку **Пересчитать**.

   В поле **Значение** будет показано, что оценка выражения XPath дает значение `true`.

## <a name="see-also"></a>См. также

- [Отладка XSLT](../xml-tools/debugging-xslt.md)
