---
title: Установка визуализатора | Документация Майкрософт
ms.date: 06/10/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6410e9ba1250da5a0a247c786e4aada310186c4a
ms.sourcegitcommit: da7f093db52df5dcd67e0a030e616b307f0dc2a8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91211369"
---
# <a name="how-to-install-a-visualizer"></a>Практическое руководство. Установка визуализатора
После создания визуализатора необходимо установить его так, чтобы он стал доступен в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Установка визуализатора — это простой процесс.

> [!NOTE]
> В приложениях UWP поддерживаются только стандартные текстовые визуализаторы, а также визуализаторы HTML, XML и JSON. Пользовательские визуализаторы (то есть, созданные пользователем) не поддерживаются.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Установка визуализатора для Visual Studio 2019

1. Найдите библиотеку DLL, содержащую построенный визуализатор.

   Как правило, лучше всего, если DLL-библиотека на стороне отладчика и библиотека DLL отлаживаемой стороны указывают **любой ЦП** в качестве целевой платформы. DLL-библиотека на стороне отладчика должна быть либо **любым ЦП**, либо **32-битным**. Целевая платформа для библиотеки DLL на стороне отлаживаемого объекта должна соответствовать процессу отладки.

2. Скопируйте DLL [стороны отлаживаемого объекта](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (и все библиотеки DLL, от которых она зависит) в одно из следующих расположений:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Скопируйте DLL [стороны отлаживаемого объекта](create-custom-visualizers-of-data.md#to-create-the-visualizer-object-source-for-the-debuggee-side) в одно из следующих расположений:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\` *VisualStudioVersion* `\Visualizers\` *Framework*

    где *Framework* является одним из следующих:
    - `net2.0` для отлаживаемого объекта, выполняющего среду выполнения `.NET Framework`.
    - `netstandard2.0` для отлаживаемого объекта с использованием среды выполнения, поддерживающей `netstandard 2.0` (`.NET Framework v4.6.1+` или `.NET Core 2.0+`).
    - `netcoreapp` для отлаживаемого объекта, выполняющего среду выполнения `.NET Core`. (поддерживает `.NET Core 2.0+`)

   Библиотека DLL на стороне отлаживаемого объекта необходима, если требуется создать автономный визуализатор. Эта библиотека DLL содержит код для объекта данных, который может реализовывать методы <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.

   Если вы отлаживаете различные типы кода на стороне отлаживаемого объекта, его библиотека DLL должна быть помещена в папку для минимально поддерживаемых TFM.

4. Перезапустите сеанс отладки.

> [!NOTE]
> Процедура отличается в Visual Studio 2017 и более ранних версиях. См. [предыдущую версию](how-to-install-a-visualizer.md?view=vs-2017&preserve-view=true) этой статьи.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Установка визуализатора для Visual Studio 2017 или более поздней версии

> [!IMPORTANT]
> В Visual Studio 2017 и более ранних версиях поддерживаются только визуализаторы .NET Framework.

1. Найдите библиотеку DLL, содержащую построенный визуализатор.

2. Скопируйте библиотеку DLL в одно из следующих мест:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Перезапустите сеанс отладки.

> [!NOTE]
> Если нужно использовать визуализатор управляемого кода для удаленной отладки, скопируйте DLL по тому же пути на удаленном компьютере.
::: moniker-end

## <a name="see-also"></a>См. также
- [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)
- [Практическое руководство. Написание визуализатора](create-custom-visualizers-of-data.md)
