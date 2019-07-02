---
title: Аннотация структур и классов
ms.date: 06/28/2019
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
- _Field_z_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 35be465064c9524eb0e1339794b6a19b7a595da1
ms.sourcegitcommit: d2b234e0a4a875c3cba09321cdf246842670d872
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2019
ms.locfileid: "67493634"
---
# <a name="annotating-structs-and-classes"></a>Аннотация структур и классов

Вы можете добавить примечание к структурам и членам классов, используя примечания, которые действуют как инварианты — предполагается, что они будут выполнены в любом вызове функции или функции входа и выхода, которая содержит включающую структуру в качестве значения параметров или результатов.

## <a name="struct-and-class-annotations"></a>Структура и класс заметки

- `_Field_range_(low, high)`

     Поле находится в диапазоне (включительно) из `low` для `high`.  Эквивалент для `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` применяется к аннотированному объекту с помощью соответствующих предусловий или постусловий.

- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     Поле с записываемым размером в элементах (или байтах), как определено в `size`.

- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     Поле с записываемым размером в элементах (или байтах), как определено в `size` и `count` этих элементов (байт), которые доступны для чтения.

- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     Поле с размером в элементах (или байт), доступных для записи и чтения, как определено в `size`.

- `_Field_z_`

     Поле, содержащее строку, завершающуюся символом null.

- `_Struct_size_bytes_(size)`

     Применяется к объявлению структуры или класса.  Указывает, что допустимый объект этого типа может быть больше объявленного типа с количеством байт, указанным в `size`.  Пример:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     Размер буфера в байтах параметра `pM` типа `MyStruct *` затем принимается:

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="example"></a>Пример

```cpp
#include <sal.h>
// For FIELD_OFFSET macro
#include <windows.h>

// This _Struct_size_bytes_ is equivalent to what below _Field_size_ means.
_Struct_size_bytes_(FIELD_OFFSET(MyBuffer, buffer) + bufferSize * sizeof(int))
struct MyBuffer
{
    static int MaxBufferSize;
    
    _Field_z_
    const char* name;
    
    int firstField;

    // ... other fields

    _Field_range_(1, MaxBufferSize)
    int bufferSize;
    _Field_size_(bufferSize)        // Prefered way - easier to read and maintain.
    int buffer[0];
};
```

Примечания в этом примере:

- `_Field_z_` равно `_Null_terminated_`.  `_Field_z_` для имени поля указывает, что в поле имени строку, завершающуюся символом null.
- `_Field_range_` для `bufferSize` указывает, что значение `bufferSize` не может превышать 1 и `MaxBufferSize` (оба числа включительно).
- Конечные результаты из `_Struct_size_bytes_` и `_Field_size_` заметки являются эквивалентными. Для структур или классов, которые имеют аналогичный макет `_Field_size_` проще читать и обслуживать, так как она содержит меньшее число ссылок и вычислений, чем эквивалент `_Struct_size_bytes_` заметки. `_Field_size_` не требует преобразования в размер в байтах. Если размер в байтах является единственным параметром, например, для поля указателя типа void, `_Field_size_bytes_` может использоваться. Если оба `_Struct_size_bytes_` и `_Field_size_` существует, оба будут доступны для средства. Возлагается средство что делать, если две заметки не согласен.

## <a name="see-also"></a>См. также

- [Использование аннотаций SAL для уменьшения количества дефектов в коде C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Основные сведения о языке SAL](../code-quality/understanding-sal.md)
- [Создание примечаний к параметрам и возвращаемым значениям функций](../code-quality/annotating-function-parameters-and-return-values.md)
- [Аннотация поведения функций](../code-quality/annotating-function-behavior.md)
- [Аннотация поведения блокировки](../code-quality/annotating-locking-behavior.md)
- [Указание времени и места применения примечания](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Встроенные функции](../code-quality/intrinsic-functions.md)
- [Рекомендации и примеры](../code-quality/best-practices-and-examples-sal.md)