---
title: Идебугсимболпровидердирект | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 29f0e7e3d2fefe0f47dc971ebff273bf2745a5ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909425"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Представляет поставщик символов, который имеет прямой доступ к метаданным и основным интерфейсам символов.

## <a name="syntax"></a>Синтаксис

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>Методы
 Этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Получает идентификатор домена приложения по указанному адресу отладки.|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Извлекает сведения о модулях в группе символов.|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Извлекает сведения о группе символов, членом которой является поставщик символов.|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Извлекает сведения об импорте метаданных.|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Извлекает сведения о методе по указанному адресу отладки.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Извлекает средство чтения символов для неуправляемого кода.|

## <a name="remarks"></a>Remarks
 Этот интерфейс можно использовать вместо большинства других интерфейсов поставщика символов. Он предоставляет прямой доступ к метаданным и `CorSym` интерфейсам.

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
