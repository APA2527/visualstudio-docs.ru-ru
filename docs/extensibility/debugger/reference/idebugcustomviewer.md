---
title: IDebugCustomViewer | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46561bbab71b12d924edec96650736c8b1576894
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328035"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Этот интерфейс позволяет вычислитель выражений (EE) для отображения значения свойства в формате необходим.

## <a name="syntax"></a>Синтаксис

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
EE реализует этот интерфейс для отображения значения свойства в пользовательском формате.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
Вызов COM `CoCreateInstance` функция создает экземпляр этого интерфейса. `CLSID` Передается `CoCreateInstance` получается из реестра. Вызов [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Получает расположение в реестре. См. в разделе "Примечания" для сведений, а также пример.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Не все, что необходим для отображения заданного значения.|

## <a name="remarks"></a>Примечания
Этот интерфейс используется в том случае, если значение свойства невозможно отобразить обычным способом — например, с помощью таблицы данных или другой тип сложного свойства. Пользовательское средство просмотра, представлены `IDebugCustomViewer` интерфейсом, отличается от визуализатора типа, который является внешней программой, для отображения данных определенного типа независимо от того, EE. EE реализует пользовательское средство просмотра, относящиеся к этой EE. Пользователь выбирает, какой тип визуализатора для использования, будь то тип визуализатора или пользовательское средство просмотра. См. в разделе [визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) Дополнительные сведения об этом процессе.

Пользовательское средство просмотра регистрируется в так же, как EE и, следовательно, требует GUID языка и GUID поставщика. Точные метрики (или имя записи реестра) известна только EE. Эта метрика возвращается в [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) структуру, которая в свою очередь, возвращается путем вызова [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Значение, хранимое в метрики равно `CLSID` , передаваемое в COM `CoCreateInstance` функцию (см. пример).

[Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) функции `SetEEMetric`, можно использовать для регистрации пользовательское средство просмотра. См. в разделе реестра «Вычислители выражений» `Debugging SDK Helpers` для определенного реестра клавиш, требуется пользовательское средство просмотра. Обратите внимание, что пользовательское средство просмотра требуется только одна метрика, (который определяется с исполнитель EE), то время как вычислитель выражений требует несколько предварительно определенных метрик.

Как правило, пользовательское средство просмотра предоставляет только для чтения представление данных, поскольку [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) предоставленный интерфейс [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) не имеет методов для изменения значения свойства, за исключением как строка. Чтобы обеспечить поддержку изменения блоков произвольных данных, EE реализует пользовательский интерфейс на тот же объект, реализующий `IDebugProperty3` интерфейс. Затем этот пользовательский интерфейс содержит методы, необходимые для изменения произвольный блок данных.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример
В этом примере показано, как получить первый пользовательское средство просмотра из свойства, если это свойство имеет любые пользовательские средства просмотра.

```cpp
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)
{
    // This string is typically defined globally.  For this example, it
    // is defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugCustomViewer *pViewer = NULL;
    if (pProperty != NULL) {
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);
        if (pProperty3 != NULL) {
            HRESULT hr;
            ULONG viewerCount = 0;
            hr = pProperty3->GetCustomViewerCount(&viewerCount);
            if (viewerCount > 0) {
                ULONG viewersFetched = 0;
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };
                hr = pProperty3->GetCustomViewerList(0,
                                                     1,
                                                     &viewerInfo,
                                                     &viewersFetched);
                if (viewersFetched == 1) {
                    CLSID clsidViewer = { 0 };
                    CComPtr<IDebugCustomViewer> spCustomViewer;
                    // Get the viewer's CLSID from the registry.
                    ::GetEEMetric(viewerInfo.guidLang,
                                  viewerInfo.guidVendor,
                                  viewerInfo.bstrMetric,
                                  &clsidViewer,
                                  strRegistrationRoot);
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {
                        // Instantiate the custom viewer.
                        spCustomViewer.CoCreateInstance(clsidViewer);
                        if (spCustomViewer != NULL) {
                            pViewer = spCustomViewer.Detach();
                        }
                    }
                }
            }
        }
    }
    return(pViewer);
}
```

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
