---
title: 'Внутренние элементы: класс ContingentProperties | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60129950c2311cc94b8573de4cd8ae3c46194e75
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926002"
---
# <a name="contingentproperties-class---internal-members"></a>Внутренние элементы: класс ContingentProperties
Содержит дополнительные свойства для <xref:System.Threading.Tasks.Task> объекта.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в mscorlib.dll)

 Так как при отсутствии доступа к этим внутренним членам платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Участники

### <a name="fields"></a>Поля

|name|Описание|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|Список дочерних задач, которые зарегистрированы с помощью этой задачи.|

## <a name="remarks"></a>Примечания
 .NET Framework инициализирует поля этого класса, только в том случае, когда они нужны.

## <a name="see-also"></a>См. также
- [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)