---
title: Элемент Bitmap | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc1fb57c7ec43421b211b29cfd6ab97b24a1864c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184746"
---
# <a name="bitmap-element"></a>Элемент Bitmap
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет растрового изображения. Растровое изображение загружается из ресурса или из файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательный. Идентификатор GUID идентификатора GUID и идентификатора команды.<br /><br /> Атрибут guid для точечного рисунка не связан с любой VSPackage или другие группы команд.  Оно должно быть уникальным для определение битовой карты и не должны использоваться в любых других целях.|  
|Идентификатор ресурса|Идентификатор GUID и идентификатора идентификатор команды. Идентификатор ресурса или атрибут href не требуется.<br /><br /> Атрибут resID имеет целочисленный идентификатор ресурса, определяет набора точечных рисунков, который должен быть загружен во время объединения таблицы команд.  При загрузке таблицы команд, растровых изображений, заданных идентификатором ресурса будет загружаться из ресурсов одного модуля.|  
|usedList|Требуется, если присутствует атрибут resID. Выбор доступных образов в наборе точечных рисунков.|  
|href|Путь к точечному рисунку. Идентификатор ресурса или атрибут href не требуется.<br /><br /> В путь включаемых файлов выполняется поиск файла указанное изображение, внедренном в результате получается двоичный файл.  Во время слияния таблицы команд образ копируется, и поиск дополнительных ресурсов или нагрузки не требуется.  Если отсутствует атрибут usedList, доступны все образы в полосе. **Примечание.**  Изображения может быть предоставлен в одном из нескольких форматов, которые включают: bmp, PNG и GIF.  Более ранних версиях компилятора не поддерживали 32-разрядных точечных рисунков, в которых данные альфа-канала для частичную прозрачность. Решение для этих версий — использовать формат PNG.|  
|Условие|Необязательный параметр. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Bitmaps](../extensibility/bitmaps-element.md)|Группирует элементы растрового изображения.|  
  
## <a name="example"></a>Пример  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
