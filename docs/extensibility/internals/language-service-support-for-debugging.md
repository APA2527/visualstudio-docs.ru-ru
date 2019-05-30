---
title: Поддержка языковой службы для отладки | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d4946c25aeac2d677b7a527a3d2bb338db3aa31
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333648"
---
# <a name="language-service-support-for-debugging"></a>Поддержка языковой службы для отладки
Служба языка может предоставлять возможности, которые поддерживают отладчика через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> интерфейс. Их число входят проверка точек останова и предоставление список выражений среди **"Видимые"** окна.

 Тем не менее необходимо иметь вычислитель выражений для отладки вашего языка. Средство оценки выражений отвечает за вычисление выражений для получения значений во время отладки. Сведения о реализации вычислители выражений CLR см.:

- [Вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Образец средства оценки выражений управляемого](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Сообщения компилятора
 Тип компилятора определяет, что необходимо сделать для выполнения отладки для выбранного языка. Если компилятор целевой операционной системой является Windows и записывает PDB-файл, можно отлаживать программы, с помощью машинного кода, отладки ядра, который интегрирован в Visual Studio. Если компилятор создает промежуточный язык Майкрософт (MSIL), можно отлаживать программы, с помощью управляемого кода, отладка механизм, который интегрирован в Visual Studio. Если компилятор предназначено для собственных операционной системы или другой среды, необходимо написать собственный ядро отладки.

 Дополнительные сведения о реализации, отладка для языка см. в разделе [Приступая к работе](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) в пакете SDK Visual Studio отладки.