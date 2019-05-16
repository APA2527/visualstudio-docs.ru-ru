---
title: Запрос. PDB-файл | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b9013d41ac4d5ca890e7cc9e09b5eb9415cb640
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691332"
---
# <a name="querying-the-pdb-file"></a>Запрос PDB-файла
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Файл базы данных программы (с расширением PDB) — это двоичный файл, который содержит тип и символьную отладочную информацию, собранные в ходе компиляции и компоновки проекта. PDB-файл создается при компиляции программы C/C++ с **/ZI** или **/ZI** или [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], или [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] программировать **/debug** параметр. Объектные файлы содержат ссылки в PDB-файла для отладочной информации. Дополнительные сведения о PDB-файлы, см. в разделе [PDB-файлы](https://msdn.microsoft.com/1761c84e-8c2c-4632-9649-b5f99964ed3f). Приложения доступа к интерфейсу отладки можно использовать следующие общие действия для получения сведений о различных символов, объекты и элементы данных в исполняемый образ.  
  
### <a name="to-query-the-pdb-file"></a>Запрос PDB-файла  
  
1. Получения источника данных путем создания [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) интерфейс.  
  
    ```cpp#  
    CComPtr<IDiaDataSource> pSource;  
    hr = CoCreateInstance( CLSID_DiaSource,  
                           NULL,  
                           CLSCTX_INPROC_SERVER,  
                           __uuidof( IDiaDataSource ),  
                          (void **) &pSource);  
  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    ```  
  
2. Вызовите [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) или [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) загрузить отладочную информацию.  
  
    ```cpp#  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    ```  
  
3. Вызовите [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) открыть [IDiaSession](../../debugger/debug-interface-access/idiasession.md) для получения доступа к отладочной информации.  
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4. Используйте методы в `IDiaSession` запрос для символов в источнике данных.  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5. Используйте `IDiaEnum*` интерфейсы для перечисления и просмотра символы или другие элементы отладочную информацию.  
  
    ```cpp#  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )  
    {  
         // Do something with each IDiaTable.  
    }  
    ```  
  
## <a name="see-also"></a>См. также  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
