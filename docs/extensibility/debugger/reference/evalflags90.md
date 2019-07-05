---
title: EVALFLAGS90 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 24afc4456570ff0c3e5dc1eb56789984bf18ac58
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337832"
---
# <a name="evalflags90"></a>EVALFLAGS90
Перечисляет допустимые значения для флагов, которые управляют вычисления выражения. Это перечисление расширяет [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисления.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
typedef DWORD EVALFLAGS90;
```

```csharp
public enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
```

## <a name="fields"></a>Поля
`EVAL90_RETURNVALUE`\
Указывает, что возвращаемое значение, если таковое имеется, вычисляется.

`EVAL90_NOSIDEEFFECTS`\
Указывает, что побочные эффекты не разрешается.

`EVAL90_ALLOWBPS`\
Указывает остановки точек останова.

`EVAL90_ALLOWERRORREPORT`\
Указывает отчетов к узлу разрешен, об ошибках. В основном используется для вычисления выражений в скрипте в Internet Explorer.

`EVAL90_FUNCTION_AS_ADDRESS`\
Функции силы для оценки в качестве адреса, вместо вызова функции.

`EVAL90_NOFUNCEVAL`\
Запрещает вычисляется функция. Например, рассмотрим `int` маркера в выражении `myExpression(int) + 10`. Эта функция может вычисляться правильно, как адрес, а не как значение.

`EVAL90_NOEVENTS`\
Флаг, указывающий, что события, происходящие во время вычисления выражения не следует отправлять в диспетчер отладки сеансов (SDM) или в интегрированную среду разработки.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Позволяет вычисление выражений во время разработки.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Позволяет неявного создания переменной.

`EVAL90_FORCE_EVALUATION_NOW`\
Оценка Принудительное немедленное. Это полезно при обслуживании запроса, например запрос пользователя.

## <a name="requirements"></a>Требования
Заголовок: Msdbg90.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
