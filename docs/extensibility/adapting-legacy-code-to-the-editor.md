---
title: Адаптация кода прежних версий в редактор | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d0e9bcd9943dafc9dcbe9beb62433a62b55dc8e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62844003"
---
# <a name="adapt-legacy-code-to-the-editor"></a>Адаптировать устаревшего кода в редакторе
В редакторе Visual Studio имеет множество функций, которые доступны через существующие компоненты кода. Ниже показано, как адаптировать компонента не MEF, например, пакет VSPackage, использовать функциональные возможности редактора. Инструкции также показано, как использовать адаптеры для получения служб редактора в управляемом и неуправляемом коде.

## <a name="editor-adapters"></a>Редактор адаптеров
Редактор адаптеры, или оболочки совместимости, являются оболочками для объектов редактора, которые также предоставляют классы и интерфейсы в <xref:Microsoft.VisualStudio.TextManager.Interop> API. Можно использовать адаптеры для перемещения между службами нередактирующему, например, команды оболочки Visual Studio и служб редактора. (Это как редактор размещена в Visual Studio.) Адаптеры также расширения устаревших редактора и языковой службы для правильной работы в Visual Studio.

## <a name="use-editor-adapters"></a>Использовать редактор адаптера
<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> Предоставляет методы, которые переключаются между новый редактор интерфейсов и устаревшие интерфейсы, а также методы, которые создают адаптеров.

Если вы используете эту службу в части компонента MEF, можно импортировать службы следующим образом.

```
[Import(typeof(IVsEditorAdaptersFactoryService))]
internal IVsEditorAdaptersFactoryService editorFactory;
```

Если вы хотите использовать эту службу в компоненте не MEF, следуйте инструкциям в разделе «С помощью Visual Studio редактор служб в MEF не компонент» далее в этом разделе.

## <a name="switch-between-the-new-editor-api-and-the-legacy-api"></a>Переключаться между новый редактор API и старый API
Используйте следующие методы для переключения между объектом редактора и устаревшего интерфейса.

|Метод|Преобразование|
|------------|----------------|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Преобразует <xref:Microsoft.VisualStudio.Text.ITextBuffer> для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Преобразует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> для <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Преобразует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> для <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Преобразует <xref:Microsoft.VisualStudio.Text.Editor.ITextView> для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Преобразует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|

## <a name="create-adapters"></a>Создание адаптеров
Используйте следующие методы для создания адаптеров для устаревшие интерфейсы.

|Метод|Преобразование|
|------------|----------------|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> для указанного <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|

## <a name="creating-adapters-in-unmanaged-code"></a>Создание адаптеров в неуправляемом коде
Все классы адаптеров регистрируются локальным воссоздаваемым и может быть создан с помощью `VsLocalCreateInstance()` функции.

Все адаптеры создаются с помощью идентификаторов GUID, которые определены в *vsshlids.h* файл *\..\VisualStudioIntegration\Common\Inc\\* папку пакета SDK для Visual Studio Установка. Чтобы создать экземпляр VsTextBufferAdapter, используйте следующий код.

```
IVsTextBuffer *pBuf = NULL;
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);
```

## <a name="create-adapters-in-managed-code"></a>Создание адаптеров в управляемом коде
В управляемом коде совместно созданием адаптеры таким же образом, описанного для неуправляемого кода. Также можно использовать службу MEF, которое служит для создания и взаимодействия с адаптерами. Таким способом получения адаптер обеспечивает более точный контроль меньше, чем при ее создании совместно.

### <a name="to-create-an-adapter-for-ivstextview"></a>Чтобы создать адаптер для IVsTextView

1. Добавьте ссылку на *Microsoft.VisualStudio.Editor.dll*. Убедитесь, что `CopyLocal` присваивается `false`.

2. Создать экземпляр <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, как показано ниже.

    ```
    using Microsoft.VisualStudio.Editor;
    ...
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();
    ```

3. Вызовите метод `CreateX()`.

    ```
    adapterFactoryService.CreateTextViewAdapter(textView);
    ```

## <a name="use-the-visual-studio-editor-directly-from-unmanaged-code"></a>Использовать редактор Visual Studio непосредственно из неуправляемого кода
Имен Microsoft.VisualStudio.Platform.VSEditor и Microsoft.VisualStudio.Platform.VSEditor.Interop предоставляют вызываемые средствами COM интерфейсы как интерфейсы IVx *. Например, интерфейс Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer версия COM <xref:Microsoft.VisualStudio.Text.ITextBuffer> интерфейс. Из `IVxTextBuffer`, можно получить доступ к моментальным снимкам буфера, меняющим содержимое буфера, прослушивать события изменения текста в буфере и создание точек отслеживания и диапазонов. Ниже показано, как получить доступ к `IVxTextBuffer` из `IVsTextBuffer`.

### <a name="to-get-an-ivxtextbuffer"></a>Для получения IVxTextBuffer

1. Определения IVx\* интерфейсы являются в *VSEditor.h* файл *\..\VisualStudioIntegration\Common\Inc\\* папку в Visual Studio Установка пакета SDK.

2. Следующий код создает экземпляр текстового буфера, используя `IVsUserData->GetData()` метод. В следующем коде `pData` — это указатель на `IVsUserData` объект.

    ```cpp
    #include <textmgr.h>
    #include <VSEditor.h>
    #include <vsshlids.h>

    CComPtr<IVsTextBuffer> pVsTextBuffer;
    CComPtr<IVsUserData> pData;
    CComPtr<IVxTextBuffer> pVxBuffer;
    ...
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))
    {
        CComVariant vt;
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))
        {
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);
        }
    }
    ```

## <a name="use-visual-studio-editor-services-in-a-non-mef-component"></a>Использование служб редактора Visual Studio в компоненте не MEF
Если у вас есть существующий компонент управляемого кода, не использующей MEF, и вы хотите использовать службы в редакторе Visual Studio, необходимо добавить ссылку на сборку, содержащую ComponentModelHost VSPackage и получить его модели SComponentModel службу.

### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Для использования компонентов редактора Visual Studio из компонента не MEF

1. Добавьте ссылку на *Microsoft.VisualStudio.ComponentModelHost.dll* сборки в *\..\Common7\IDE\\* папке установки Visual Studio. Убедитесь, что `CopyLocal` присваивается `false`.

2. Добавьте закрытый `IComponentModel` член в класс, в котором вы хотите использовать службы редактора Visual Studio, как показано ниже.

    ```
    using Microsoft.VisualStudio.ComponentModelHost;
    ....
    private IComponentModel componentModel;
    ```

3. Создайте экземпляр модели компонентов в методе инициализации компонента.

    ```
    componentModel =
        (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));
    ```

4. После этого любой из служб редактора Visual Studio можно получить, вызвав `IComponentModel.GetService<T>()` метод для службы.

    ```
    textBufferFactoryService =
        componentModel.GetService<ITextBufferFactoryService>();
    ```
