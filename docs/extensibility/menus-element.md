---
title: Элемент Menus | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: d825a99b-e05c-4dd9-8933-a180216d667a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef5124bc59a4eb0671ba5493f79ea301aa48fc71
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346626"
---
# <a name="menus-element"></a>Элемент меню
Определяет, меню и панелей инструментов, реализующий VSPackage.

## <a name="syntax"></a>Синтаксис

```xml
<Menus>
  <Menu>... </Menu>
  <Menu>... </Menu>
</Menus>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|Условие|Необязательный параметр. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент меню](../extensibility/menus-element.md)|Определяет, меню и панелей инструментов, реализующий VSPackage.|
|[Элемент меню](../extensibility/menu-element.md)|Представляет один меню или панели инструментов.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент Commands](../extensibility/commands-element.md)|Представляет коллекцию команд в VSPackage.|

## <a name="example"></a>Пример

```xml
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>См. также
- [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)