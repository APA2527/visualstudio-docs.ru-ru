---
title: Установка пакета SDK для Visual Studio | Документация Майкрософт
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 664ecb57a326938345c2c313228c813293230b7e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910594"
---
# <a name="install-the-visual-studio-sdk"></a>Установка пакета SDK для Visual Studio

Visual Studio SDK (пакет средств разработки программного обеспечения) является дополнительным компонентом в программе установки Visual Studio. VS SDK также можно установить позже.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Установить пакет SDK для Visual Studio как часть установки Visual Studio

Чтобы включить VS SDK в установку Visual Studio, установите **разработка расширений Visual Studio** рабочей нагрузки в разделе **другие наборы инструментов**. Эта рабочая нагрузка будет установить пакет SDK для Visual Studio и все необходимые условия. Выполнить более глубокую настройку установки, установив или сняв компоненты из **Сводка** представления.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Установить пакет SDK для Visual Studio после установки Visual Studio

Чтобы установить пакет SDK для Visual Studio после завершения установки Visual Studio, перезапустите установщик Visual Studio и выберите **разработка расширений Visual Studio** рабочей нагрузки.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Установите пакет SDK для Visual Studio из решения

При открытии решения с проектом расширения без предварительной установки VS SDK, вам будет предложено по **установить функции отсутствующих** диалогового окна, чтобы установить **разработка расширений Visual Studio** Рабочая нагрузка:

![Установить расширение разработки](../extensibility/media/install-extension-development.png "установить разработка расширения")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Установите пакет SDK для Visual Studio из командной строки

С любой рабочей нагрузки Visual Studio или компонента, вы можете также установить **разработка расширений Visual Studio** рабочей нагрузки (идентификатор: Microsoft.VisualStudio.Workload.VisualStudioExtension) из командной строки. См. в разделе [использование параметров командной строки для установки Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) Дополнительные сведения о параметрах командной строки и общие инструкции по определению идентификаторы рабочей нагрузки или компонента.

Обратите внимание на то, что необходимо использовать установщик Visual Studio, который соответствует установленной версии Visual Studio. Например, если у вас есть Visual Studio Enterprise, установленной на компьютере, необходимо запустить установщик Visual Studio Enterprise (*vs_enterprise.exe*).