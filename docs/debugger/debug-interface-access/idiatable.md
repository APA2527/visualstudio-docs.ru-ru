---
title: IDiaTable | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 604c68ef82f66358238f94b43f000fae24a076f1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62834156"
---
# <a name="idiatable"></a>IDiaTable
Перечисляет таблицы источника данных доступа к интерфейсу отладки.

## <a name="syntax"></a>Синтаксис

```
IDiaTable : IEnumUnknown
```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
В следующей таблице показаны методы `IDiaTable`.

|Метод|Описание|
|------------|-----------------|
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Извлекает [интерфейса IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) версии этот перечислитель.|
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Извлекает имя таблицы.|
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Получает число элементов в таблице.|
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Извлекает ссылку на индекс определенной записи.|

## <a name="remarks"></a>Примечания
Этот интерфейс реализует `IEnumUnknown` методы перечисления в пространстве имен Microsoft.VisualStudio.OLE.Interop. `IEnumUnknown` Интерфейс перечисления является более эффективным для перебора содержимого таблицы чем [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) и [IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md) методы.

Интерпретация `IUnknown` интерфейс возвращаемый либо `IDiaTable::Item` метод или `Next` метод (в пространстве имен Microsoft.VisualStudio.OLE.Interop) зависит от типа таблицы. Например если `IDiaTable` интерфейс представляет список внедренного источников `IUnknown` интерфейса должны запрашиваться для [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
Получить этот интерфейс, вызвав [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md) или [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md) методы.

Следующие интерфейсы реализуются с помощью `IDiaTable` интерфейса (то есть вы можете запросить `IDiaTable` интерфейс для одного из следующих интерфейсов):

- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

## <a name="example"></a>Пример
Первая функция, `ShowTableNames`, отображаются имена всех таблиц в сеансе. Вторая функция `GetTable`, выполняет все таблицы для таблицы, который реализует указанный интерфейс. Третья функция `UseTable`, показано, как использовать `GetTable` функции.

> [!NOTE]
> `CDiaBSTR` — Это класс, который заключает в оболочку `BSTR` и автоматически обрабатывает освобождение строки, когда экземпляр выходит из области.

```C++
void ShowTableNames(IDiaSession *pSession)
{
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )
            && celt == 1 )
    {
        CDiaBSTR bstrTableName;
        if ( pTable->get_name( &bstrTableName ) != 0 )
        {
            Fatal( "get_name" );
        }
        printf( "Found table: %ws\n", bstrTableName );
    }

// Searches the list of all tables for a table that supports
// the specified interface.  Use this function to obtain an
// enumeration interface.
HRESULT GetTable(IDiaSession* pSession,
                 REFIID       iid,
                 void**       ppUnk)
{
    CComPtr<IDiaEnumTables> pEnumTables;
    HRESULT hResult;

    if (FAILED(pSession->getEnumTables(&pEnumTables)))
        Fatal("getEnumTables");

    CComPtr<IDiaTable> pTable;
    ULONG celt = 0;
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&
           celt == 1)
    {
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)
        {
            return S_OK;
        }
        pTable = NULL;
    }

    if (FAILED(hResult))
        Fatal("EnumTables->Next");

    return E_FAIL;
}

// This function shows how to use the GetTable function.
void UseTable(IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pEnumSegments;
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))
    {
        // Do something with pEnumSegments.
    }
}
```

## <a name="requirements"></a>Требования
Заголовок: dia2.h

Библиотека: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>См. также
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
- [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
