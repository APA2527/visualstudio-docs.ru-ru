---
title: Обзор (доступа к интерфейсу отладки пакета SDK) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7374b03da42e34e8ac3be8c7cc570769d9cfd1ff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179200"
---
# <a name="overview-debug-interface-access-sdk"></a>Общие сведения (SDK для доступа к интерфейсу отладки)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Используйте пакет SDK для доступа к данным отладки Microsoft. Пакет SDK для доступа к интерфейсу отладки предоставляет COM набор API, который избавляет от необходимости изменять код каждый раз, когда Майкрософт изменяет формат отладочной информации. Пакет SDK для доступа к интерфейсу отладки также позволяет считывать из набор select отладочной информации в PDB-файл и .dbg файлы, созданные на предыдущих версиях [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 5.0 и более поздних версиях.  
  
 Каждый интерфейс в пакете SDK для доступа к интерфейсу отладки представляет объект COM, за исключением там, где указано обратное. Дополнительные интерфейсы и тем самым дополнительные объекты, созданные с помощью явных запросов, такие как [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) или [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), а не путем вызова `QueryInterface` на существующие указатели интерфейса.  
  
## <a name="see-also"></a>См. также  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
