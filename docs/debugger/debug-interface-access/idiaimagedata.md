---
title: IDiaImageData | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData interface
ms.assetid: b696f350-fc08-4352-9287-a15e87512c1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1e3dd8c395c59bc3255c1c9ee55837466c1cef7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828514"
---
# <a name="idiaimagedata"></a>IDiaImageData
Предоставляет сведения о базового смещения расположения и памяти модуля или изображения.

## <a name="syntax"></a>Синтаксис

```
IDiaImageData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
В следующей таблице показаны методы `IDiaImageData`.

|Метод|Описание|
|------------|-----------------|
|[IDiaImageData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-relativevirtualaddress.md)|Извлекает расположение виртуальной памяти модуля относительно приложения.|
|[IDiaImageData::get_virtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-virtualaddress.md)|Извлекает расположение изображения в виртуальной памяти.|
|[IDiaImageData::get_imageBase](../../debugger/debug-interface-access/idiaimagedata-get-imagebase.md)|Получает область памяти, в котором должно основываться изображение.|

## <a name="remarks"></a>Примечания
Некоторые потоки отладки (XDATA, PDATA) содержат копии данных, также сохраняются в образе. Эти потоковую передачу данных, можно запрашивать объекты `IDiaImageData` интерфейс. В этом разделе сведения в разделе «Примечания для вызывающих объектов».

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
Получить этот интерфейс, вызвав `QueryInterface` на [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) объекта. Обратите внимание, что не все отладочные потоки поддержки `IDiaImageData` интерфейс. Например, в настоящее время поддерживает только потоки XDATA и PDATA `IDiaImageData` интерфейс.

## <a name="example"></a>Пример
В этом примере выполняется поиск всего потоки отладки для любого потока, который поддерживает `IDiaImageData` интерфейс. При обнаружении такой поток отображается некоторые сведения об этом потоке.

```C++
void ShowImageData(IDiaSession *pSession)
{
    if (pSession != NULL)
    {
        CComPtr<IDiaEnumDebugStreams> pStreamsList;
        HRESULT hr;

        hr = pSession->getEnumDebugStreams(&pStreamsList);
        if (SUCCEEDED(hr))
        {
            LONG numStreams = 0;
            hr = pStreamsList->get_Count(&numStreams);
            if (SUCCEEDED(hr))
            {
                ULONG fetched = 0;
                for (LONG i = 0; i < numStreams; i++)
                {
                    CComPtr<IDiaEnumDebugStreamData> pStream;
                    hr = pStreamsList->Next(1,&pStream,&fetched);
                    if (fetched == 1)
                    {
                        CComPtr<IDiaImageData> pImageData;
                        hr = pStream->QueryInterface(__uuidof(IDiaImageData),
                                                     (void **)&pImageData);
                        if (SUCCEEDED(hr))
                        {
                            CComBSTR name;
                            hr = pStream->get_name(&name);
                            if (SUCCEEDED(hr))
                            {
                                wprintf(L"Stream %s:\n",(BSTR)name);
                            }
                            else
                            {
                                wprintf(L"Failed to get name of stream\n");
                            }

                            ULONGLONG imageBase = 0;
                            if (pImageData->get_imageBase(&imageBase) == S_OK)
                            {
                                wprintf(L"  image base = 0x%0I64x\n",imageBase);
                            }

                            DWORD relVA = 0;
                            if (pImageData->get_relativeVirtualAddress(&relVA) == S_OK)
                            {
                                wprintf(L"  relative virtual address = 0x%08lx\n",relVA);
                            }

                            ULONGLONG va = 0;
                            if (pImageData->get_virtualAddress(&va) == S_OK)
                            {
                                wprintf(L"  virtual address = 0x%0I64x\n", va);
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="requirements"></a>Требования
Заголовок: dia2.h

Библиотека: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>См. также
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
