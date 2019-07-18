---
title: Отображение локальных переменных | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cdbba0cfa48792127accc71cba75f8542556d67
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63409378"
---
# <a name="displaying-locals"></a>Отображение локальных переменных
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Выполнение всегда выполняется в контексте метода, также известный как содержащего метода или текущий метод. Когда выполнение приостанавливается, Visual Studio вызывает модуль отладки (DE), чтобы получить список локальных переменных и аргументов, которые в совокупности называются локальные переменные метода. Visual Studio отображает эти локальные переменные и их значения в **"Локальные"** окна.  
  
 Чтобы отобразить "Локальные", вызывает DE [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) метода, принадлежащего объекту EE и присваивает ему контекст вычисления, который является, поставщика символов (SP), текущий адрес выполнения и объект связывателя. Дополнительные сведения см. в разделе [контекст оценки](../../extensibility/debugger/evaluation-context.md). Если вызов завершается успешно, `IDebugExpressionEvaluator::GetMethodProperty` возвращает [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, который представляет метод, который содержит адрес текущего выполнения.  
  
 Вызовы DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) для получения [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) объекта, который является отфильтрованы, чтобы возвращать только локальные переменные и перечислить для создания списка [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)структуры. Каждая структура содержит имя, тип и значения локальной переменной. Тип и значение хранятся в виде форматированных строк, подходящее для отображения. Имя, тип и значение обычно отображаются вместе в одной строке **"Локальные"** окна.  
  
> [!NOTE]
> **"Быстрая проверка"** и **Watch** окнах также отображаются переменные с тот же формат, имя, значение и тип. Тем не менее, эти значения получаются путем вызова [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) вместо `IDebugProperty2::EnumChildren`.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Пример реализации локальных переменных](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Используются примеры для пошагового выполнения процесс реализации "Локальные".  
  
## <a name="related-sections"></a>Связанные разделы  
 [Контекст вычислений](../../extensibility/debugger/evaluation-context.md)  
 Объясняет, что когда модуль отладки (DE) вызывает средство оценки выражений (EE), он передает три аргумента.  
  
## <a name="see-also"></a>См. также  
 [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
