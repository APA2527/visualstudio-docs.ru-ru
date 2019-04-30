---
title: Схема для расширения отладчика | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e02bfd8b528c484518816589f4f3e0e19bfa8c94
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913204"
---
# <a name="roadmap-for-extending-the-debugger"></a>Схема для расширения отладчика
Эта документация содержит руководства и справочную информацию для расширения [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] отладчика с [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отладка документации включает примеры, является полным Справочником и несколько репрезентативных сценариев, демонстрирующие типичные способы настройки отладчика.

 Компилятор и результаты ее выполнения определить, что необходимо для настройки отладки в ваш продукт. Если компилятор:

- Предназначен для собственную операционную систему Windows и записывает *. PDB-ФАЙЛ* файл, можно отлаживать программы, с помощью обработчика отладки машинного кода (DE), интегрированной в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Не нужно реализовать средства DE или выражение для оценки. Средство оценки выражений записывается синтаксис языка программирования C++.

- Создает выходной промежуточного языка MSIL, можно отлаживать программы, с помощью обработчика отладки управляемого кода DE, который также интегрируется в Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Таким образом требуется реализовать только вычислитель выражений. Средство оценки выражений образец предоставляется автоматически. Дополнительные сведения см. в следующих разделах:

   [Вычисление выражений](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Вычисление выражений](../../extensibility/debugger/evaluating-expressions.md)

   [Контекст вычисления выражений](../../extensibility/debugger/expression-evaluation-context.md)

   [Вычисление выражений в режиме приостановки выполнения](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Запись общих вычислителя выражений среды CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Целевые объекты защищенные авторским правом, операционная система или другой среды выполнения, необходимо написать собственный DE. Учебник, создающий простые DE, с помощью ATL COM предоставляется. Дополнительные сведения см. в следующих разделах:

   [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Учебник. Создание модуля отладки с помощью ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>См. также
- [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)