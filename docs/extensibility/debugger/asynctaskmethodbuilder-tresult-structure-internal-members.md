---
title: 'AsyncTaskMethodBuilder&lt;TResult&gt; внутренние элементы: структура | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c944671b3bdb42f72928822903ccb05742401f7e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350977"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; внутренних членов - структуры
В этом разделе описывается внутренним членам объектов <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> класс. Общие сведения об этом классе см. в разделе <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> справочника.

 **Пространство имен:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Сборка:** mscorlib (в mscorlib.dll)

 Так как при отсутствии доступа к этим внутренним членам платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Внутренние элементы

|name|Описание|
|----------|-----------------|
|[Свойство ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Возвращает объект, который может использоваться для уникальной идентификации этого построителя к отладчику.|
|[m_task field](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Представляет отложенной инициализацией встроенных задач.|

## <a name="see-also"></a>См. также
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)