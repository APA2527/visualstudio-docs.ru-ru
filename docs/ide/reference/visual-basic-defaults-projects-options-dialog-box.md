---
title: Страница "Параметры Visual Basic по умолчанию", папка "Проекты", диалоговое окно "Параметры"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5aedaf5c31eca900ec1730622dfc7ff6f026a61a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789139"
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>Страница "Параметры Visual Basic по умолчанию", папка "Проекты", диалоговое окно "Параметры"
Задает значения по умолчанию для параметров проекта Visual Basic. При создании проекта указанные операторы option добавляются в заголовок проекта в редакторе кода. Эти параметры применяются ко всем проектам Visual Basic.

 Чтобы открыть это диалоговое окно, в меню **Сервис** выберите **Параметры**, разверните папку **Проекты и решения** и выберите **Параметры Visual Basic по умолчанию**.

 **Option Explicit**

 Задает значение компилятора по умолчанию, чтобы требовались явные объявления переменных. По умолчанию **Option Explicit** имеет значение **On**. Дополнительные сведения см. в описании [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).

 **Option Strict**

 Задает значение компилятора по умолчанию, чтобы требовались явные сужающие преобразования, а позднее связывание было запрещено. По умолчанию **Option Strict** имеет значение **Off**. Дополнительные сведения см. в описании [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).

 **Option Compare**

 Задает значение компилятора по умолчанию для сравнения строк: двоичный файл (с учетом регистра) или текст (без учета регистра). По умолчанию **Option Compare** имеет значение **Binary**. Дополнительные сведения см. в описании [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).

 **Option Infer**

 Задает значение компилятора по умолчанию для вывода локального типа. По умолчанию **Option Infer** имеет значение **On** для вновь созданных проектов и **Off** для проектов, перенесенных из более ранних версий Visual Basic. Дополнительные сведения см. в описании [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).

## <a name="see-also"></a>См. также раздел

- [Решения и проекты](../../ide/solutions-and-projects-in-visual-studio.md)