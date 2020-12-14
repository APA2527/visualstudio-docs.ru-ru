---
title: Страница "Параметры Visual Basic по умолчанию", папка "Проекты", диалоговое окно "Параметры"
description: Сведения о том, как с помощью страницы "Параметры Visual Basic по умолчанию" в разделе "Проекты и решения" задать значения по умолчанию для параметров проекта Visual Basic.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f761161f2ad29be994b3a6260bafe827a41fabe0
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616360"
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
