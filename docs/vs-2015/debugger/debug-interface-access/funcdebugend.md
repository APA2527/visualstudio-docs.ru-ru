---
title: FuncDebugEnd | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- FuncDebugEnd symbol
- debugging [DIA SDK], end point
ms.assetid: 68f84fff-7cd3-4636-b929-7063a45009f8
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa95b9001fe1d0b38da686cf60f1a291cc6cb5df
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704844"
---
# <a name="funcdebugend"></a>FuncDebugEnd
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Если функция имеет определенные точки, в какие отладки до конца, отладки, начальная точка определяется символ с `SymTagFuncDebugEnd` тега.  
  
## <a name="properties"></a>Свойства  
 Ниже приведены свойства, которые являются допустимыми для данного типа символов.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Часть смещения расположения; Дополнительные сведения см. в разделе [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Раздел частью расположение; Дополнительные сведения см. в разделе [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` Если эта функция использует пользовательское соглашение об именовании (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` Если функция выполняет гораздо возвращаемого значения (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` Если функция содержит отклик на прерывание (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` Если функция является статическим (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ для внешней функции.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор лексической родительского символа.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Конечные точки имеют статического расположения; Дополнительные сведения см. в разделе [расположения символов](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` Если были указаны функции [noinline](https://msdn.microsoft.com/library/f259d55b-dec7-4bde-8cf9-14521e4fdc42) атрибут (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` Если были указаны функции [noreturn](https://msdn.microsoft.com/library/9c6517e5-22d7-4051-9974-3d2200ae4d1d) атрибут (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` Если функция никогда не вызывается (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Смещение символа в памяти; Дополнительные сведения см. в разделе [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel`.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` Если функция содержит сведения об отладке для оптимизированного кода (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Относительное положение в конец этой функции в пределах его модуля.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Возвращает `SymTagFuncDebugEnd` (один из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения).|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Позиция для данной функции в исполняемом образе.|  
  
## <a name="see-also"></a>См. также  
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)   
 [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)
