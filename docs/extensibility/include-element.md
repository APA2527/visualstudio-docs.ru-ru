---
title: Включить элемент | Документация Майкрософт
description: Элемент include указывает файл, который можно найти по указанному пути поиска включаемых файлов для вставки в текущий файл.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6d718178bf7490d29c0668d892add4c302b8925a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893637"
---
# <a name="include-element"></a>Включить элемент
Элемент include указывает файл, который можно найти по указанному пути поиска включаемых файлов для вставки в текущий файл.  Все определенные символы и типы станут частью скомпилированного результата.

## <a name="syntax"></a>Синтаксис

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|href|Обязательный элемент. Путь к файлу заголовка:<br /><br /> href = "стдидкмд. h"|
|Условие|Необязательный элемент. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|Нет.|Отсутствует.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Коммандтабле, элемент](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды, т. е. пункты меню, меню, панели инструментов и поля со списком, которые пакет VSPackage предоставляет интегрированной среде разработки.|

## <a name="example"></a>Пример

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>См. также раздел
- [Файлы таблицы команд Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
