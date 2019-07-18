---
title: IDiaEnumDebugStreamData | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData interface
ms.assetid: e2023c32-4c05-4d0c-a0be-f016a230c788
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 378fc75c3bd392f228ea30d1736f059e0def6d52
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695896"
---
# <a name="idiaenumdebugstreamdata"></a>IDiaEnumDebugStreamData
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Предоставляет доступ к записям в поток данных отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaEnumDebugStreamData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaEnumDebugStreamData`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaEnumDebugStreamData::get__NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-newenum.md)|Извлекает [интерфейса IEnumVARIANT](https://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e) версии этот перечислитель.|  
|[IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)|Возвращает число записей в поток данных отладки.|  
|[IDiaEnumDebugStreamData::get_name](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-name.md)|Получает имя потока данных отладки.|  
|[IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)|Извлекает указанную запись.|  
|[IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)|Извлекает указанное число записей в перечисленной последовательности.|  
|[IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)|Пропускает указанное число записей в перечисленной последовательности.|  
|[IDiaEnumDebugStreamData::Reset](../../debugger/debug-interface-access/idiaenumdebugstreamdata-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[IDiaEnumDebugStreamData::Clone](../../debugger/debug-interface-access/idiaenumdebugstreamdata-clone.md)|Создает перечислитель, содержащий же перечисленной последовательности, что и текущий перечислитель.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс предоставляет поток записи в поток данных отладки. Размер и интерпретацию каждой записи зависит от записи, получается из потока данных. Фактически, этот интерфейс предоставляет доступ к байты необработанных данных в файл символов.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызовите [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md) или [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md) методов получения `IDiaEnumDebugStreamData` объекта.  
  
## <a name="example"></a>Пример  
 В этом примере показано, как получить доступ к один поток данных и ее записи.  
  
```cpp#  
void PrintStreamData(IDiaEnumDebugStreamData* pStream)  
{  
    BSTR  wszName;  
    LONG  dwElem;  
    ULONG celt    = 0;  
    DWORD cbData;  
    DWORD cbTotal = 0;  
    BYTE  data[1024];  
  
    if(pStream->get_name(&wszName) != S_OK)  
    {  
        wprintf_s(L"ERROR - PrintStreamData() get_name\n");  
    }  
    else  
    {  
        wprintf_s(L"Stream: %s", wszName);  
        SysFreeString(wszName);  
    }  
    if(pStream->get_Count(&dwElem) != S_OK)  
    {  
        wprintf(L"ERROR - PrintStreamData() get_Count\n");  
    }  
    else  
    {  
        wprintf(L"(%d)\n", dwElem);  
    }  
    while(pStream->Next(1, sizeof(data), &cbData, (BYTE *)&data, &celt) == S_OK)  
    {  
        DWORD i;  
        for (i = 0; i < cbData; i++)  
        {  
            wprintf(L"%02X ", data[i]);  
            if(i && i % 8 == 7 && i+1 < cbData)  
            {  
                wprintf(L"- ");  
            }  
        }  
        wprintf(L"| ");  
        for(i = 0; i < cbData; i++)  
        {  
            wprintf(L"%c", iswprint(data[i]) ? data[i] : '.');  
        }  
        wprintf(L"\n");  
        cbTotal += cbData;  
    }  
    wprintf(L"Summary :\n\tSizeof(Elem) = %d\n\tNo of Elems = %d\n\n",  
            cbTotal/dwElem, dwElem);  
}  
```  
  
## <a name="requirements"></a>Требования  
 Заголовок: dia2.h  
  
 Библиотека: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (пакет SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)
