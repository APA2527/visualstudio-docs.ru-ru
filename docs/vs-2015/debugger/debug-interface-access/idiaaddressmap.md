---
title: IDiaAddressMap | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 012d6b1ca06b06f56239048fee712d898a79efa9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547511"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Позволяет контролировать как пакет SDK для доступа к интерфейсу отладки рассчитывает виртуального и относительного виртуального адреса для отладки объектов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaAddressMap`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Указывает, установлен ли уже адрес карту для конкретного сеанса.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Указывает, следует ли использовать карту для преобразования символа адреса.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Указывает, включен ли на вычисления и с помощью относительных виртуальных адресов.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Позволяет клиенту включить или отключить расчет относительными виртуальными адресами.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Извлекает текущее выравнивание изображения.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Задает выравнивание изображения.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Наборы изображений заголовки, чтобы включить трансляцию относительными виртуальными адресами.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Предоставляет адрес сопоставляются поддерживают переводы макет изображения.|  
  
## <a name="remarks"></a>Примечания  
 Элемент управления, предоставляемый данным интерфейсом инкапсулируется в двух наборов данных, вы предоставляете: изображения заголовков и устраните maps. Большинство клиентов использовать [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод для нахождения правильного отладочную информацию для изображения и метод можно обычно обнаруживает все необходимые заголовки и карт самих данных. Тем не менее некоторым клиентам реализовать специализированные обработки и для поиска данных. Такие клиенты используют методы класса `IDiaAddressMap` интерфейс для предоставления доступа к интерфейсу отладки пакета SDK с результатами поиска.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Этот интерфейс доступен из объекта сеанса доступа к интерфейсу отладки. Клиент вызывает `QueryInterface` метод для доступа к интерфейсу отладки сеанса интерфейс объекта, обычно [IDiaSession](../../debugger/debug-interface-access/idiasession.md)для получения `IDiaAddressMap` интерфейс.  
  
## <a name="requirements"></a>Требования  
 Заголовок: dia2.h  
  
 Библиотека: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (пакет SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
