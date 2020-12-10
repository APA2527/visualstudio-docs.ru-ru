---
title: начало работы с анализаторами Roslyn | Документация Майкрософт
description: Используйте эти ресурсы, чтобы приступить к работе с анализаторами Roslyn в Visual Studio. включает учебник и несколько примеров.
ms.custom: SEO-VS-2020
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c63510083f227f617b2a11ddec07510ffd792433
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994359"
---
# <a name="get-started-with-roslyn-analyzers"></a>Начало работы с анализаторами Roslyn

С помощью динамических анализаторов кода, основанных на проектах в Visual Studio, авторы API могут поставлять анализ кода, зависящего от домена, как часть пакетов NuGet. Поскольку эти анализаторы работают на основе .NET Compiler Platform (с кодовым названием «Roslyn»), они могут создавать предупреждения в коде по мере ввода, прежде чем завершить строку (больше не нужно дожидаться сборки кода для обнаружения проблем). Анализаторы также могут выполнять автоматическое исправление кода в командной строке лампочки Visual Studio, чтобы вы могли немедленно выполнить очистку кода.

## <a name="get-started"></a>Начало работы

[Обзор анализаторов Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Учебник. Создание средства для анализа и исправления кода](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Добавление исправлений кода пошаговое руководство. предоставление пользователям исправлений для проблем с анализатором](/archive/msdn-magazine/2015/february/csharp-adding-a-code-fix-to-your-roslyn-analyzer)

[Roslyn анализатор реального мира](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , который можно также просмотреть в качестве [разговора](https://channel9.msdn.com/events/Build/2015/3-725)

[Несколько примеров на сайте GitHub, сгруппированных в три вида анализаторов](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>См. также раздел

- [Справочник по версии пакета платформы компилятора .NET](roslyn-version-support.md)
- [Дополнительные документы на сайте OSS для GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Правила FxCop, реализованные с анализаторами Roslyn](../code-quality/fxcop-rule-port-status.md)
