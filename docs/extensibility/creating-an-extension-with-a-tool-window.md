---
title: Создание расширения с помощью окна инструментов | Документация Майкрософт
description: Узнайте, как использовать шаблон проекта VSIX и пользовательский шаблон элемента окна инструментов для создания расширения с помощью окна инструментов.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1b03b7a4941609462fca27bebf67d8ad2a8f7044
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944925"
---
# <a name="create-an-extension-with-a-tool-window"></a>Создание расширения с помощью окна инструментов

В этой процедуре вы узнаете, как использовать шаблон проекта VSIX и пользовательский шаблон элемента **окна инструментов** для создания расширения с помощью окна инструментов.

## <a name="prerequisites"></a>Предварительные требования

 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Создание окна инструментов

1. Создайте проект VSIX с именем **фирствиндов**. Шаблон проекта VSIX можно найти в диалоговом окне " **Новый проект** ", выполнив поиск по слову "VSIX".

2. При открытии проекта добавьте шаблон элемента окна инструментов с именем **мивиндов**. В **Обозреватель решений** щелкните правой кнопкой мыши узел проекта и выберите команду **Добавить**  >  **новый элемент**. В диалоговом окне **Добавление нового элемента** перейдите в раздел расширяемость **Visual C#**  >   и выберите **настраиваемое окно инструментов**. В поле **имя** в нижней части окна измените имя файла окна инструментов на *MyWindow.CS*.

3. Выполните сборку решения и запустите отладку.

   Откроется экспериментальный экземпляр Visual Studio. Дополнительные сведения об экспериментальном экземпляре см. [в статье экспериментальный экземпляр](../extensibility/the-experimental-instance.md).

4. В экспериментальном экземпляре перейдите к **просмотру**  >  **других окон**.

   Вы увидите пункт меню для **мивиндов**. Нажмите ее.

   Вы должны увидеть окно инструментов с заголовком **мивиндов** и кнопку, говорящую на **Click Me!.**
