---
title: Использование escape-последовательностей в текстовых шаблонах
description: Узнайте, как использовать escape-последовательности в текстовых шаблонах для создания тегов текстовых шаблонов, а также для экранирования управляющих символов и кавычек в коде C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 126fe3f4e42c9c6cf0b75bf740e1e7e2c4b269ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924331"
---
# <a name="use-escape-sequences-in-text-templates"></a>Использование escape-последовательностей в текстовых шаблонах

Можно использовать escape-последовательности в текстовых шаблонах для создания тегов текстовых шаблонов и (только в коде C#) для экранирования управляющих символов и кавычек.

Чтобы напечатать открывающий и закрывающий теги для стандартного блока кода в выходном файле, необходимо экранировать теги следующим образом:

```
\<# ... \#>
```

То же самое можно сделать с другими директивами текстового шаблона и тегами блоков кода.

Если текстовый блок содержит строки, используемые для экранирования тегов текстовых шаблонов, можно использовать следующие escape-последовательности:

- Если тегу текстового шаблона предшествует четное число Escape- \\ символов (), то средство синтаксического анализа шаблонов будет включать половину экранированных символов и включать последовательность в качестве тега текстового шаблона. Например, если в текстовом шаблоне имеется четыре escape-символа, \\ в создаваемом файле будет два символа «».

- Если тегу текстового шаблона предшествует нечетное число Escape- \\ символов (), средство синтаксического анализа шаблонов будет включать половину \\ символов "" и сам тег ( \<# or #> ). Тег не считается тегом текстового шаблона.

- Если escape- \\ символ () встречается в любой другой последовательности, отличной от того, где она экранирована управляющий символ или кавычка (только в C#), символ будет выведен напрямую.

## <a name="see-also"></a>См. также раздел

- [Практическое руководство. Создание шаблонов из шаблонов с помощью escape-последовательностей](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
