---
title: Установка агентов и контроллеров тестирования
description: Узнайте, как использовать агенты Visual Studio для оркестрации тестирования с помощью Azure Test Plans или Team Foundation Server.
ms.custom: SEO-VS-2020
ms.date: 04/17/2019
ms.topic: how-to
helpviewer_keywords:
- configure test agents, test lab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 29f4951fbd64bd02c8f70b93ea319ab0d46f89e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920421"
---
# <a name="install-test-agents-and-test-controllers"></a>Установка агентов и контроллеров тестирования

Для сценариев тестирования, в которых используются Visual Studio и Azure Test Plans или Team Foundation Server (TFS), контроллер тестирования не требуется. Agents для Visual Studio позволяет выполнять оркестрацию путем обмена данными с Azure Test Plans или TFS. В сценарии может предполагаться непрерывное тестирование для рабочих процессов сборки и выпуска в Azure Test Plans или TFS.

Также рекомендуем обратить внимание на процесс [управления сборками и выпусками](use-build-or-rm-instead-of-lab-management.md). Возможно, для вас он будет удобнее, чем управление лабораториями.

## <a name="system-requirements"></a>Требования к системе

В следующей таблице указаны требования к системе для установки агента тестирования или контроллера тестирования для Visual Studio:

| Элемент | Требования |
| ---- | ------------ |
| **Агент** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 с пакетом обновления 1 (SP1)<br />Windows Server 2016: Standard и Datacenter<br />Windows Server 2012 R2 |
| **Контроллер** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 с пакетом обновления 1 (SP1)<br />Windows Server 2016: Standard и Datacenter<br />Windows Server 2012 R2 |
| **.NET Framework** | .NET Framework 4,5 |

## <a name="install-the-test-controller-and-test-agents"></a>Установка контроллера и агентов тестирования

Вы можете скачать агенты для Visual Studio по ссылке [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?q=agents). Найдите пункт *Agents для Visual Studio 2019*, выберите *Агент* или *Контроллер*, а затем нажмите *Скачать*. Чтобы установить агент или контроллер тестирования, запустите скачанный исполняемый файл.

Вы можете скачать агенты для Visual Studio 2017, Visual Studio 2015 и Visual Studio 2013 на странице [скачивания прежних версий](https://visualstudio.microsoft.com/vs/older-downloads/).

Эти установщики доступны в виде ISO-файлов, что упрощает установку на виртуальных машинах.

::: moniker range="vs-2017"
## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Совместимые версии TFS, Microsoft Test Manager, контроллера тестирования и агента тестирования

Вы можете комбинировать разные версии TFS, Microsoft Test Manager, контроллера тестирования и агента тестирования в соответствии с данными в следующей таблице.

| TFS | Microsoft Test Manager с Lab Center | Контроллер | Агент |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: обновление с 2015 или новая установка | 2017 | 2017 | 2017 |
| 2017: обновление с 2015 или новая установка | 2017 | 2013, обновление 5 | 2013, обновление 5 |
| 2017: обновление с 2015 или новая установка | 2015 | 2013, обновление 5 | 2013, обновление 5 |
| 2015: обновление с 2013 | 2013 | 2013 |2013 |
| 2015: новая установка | 2013 | 2013 | 2013 |
| 2015: обновление с 2013 или новая установка | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="compatible-versions-of-tfs-the-test-controller-and-test-agent"></a>Совместимые версии TFS, контроллера и агента тестирования

Вы можете использовать различные сочетания версий TFS, контроллера тестирования и агента тестирования согласно следующей таблице.

| TFS | Контроллер | Агент |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: обновление с 2015 или новая установка | 2017 | 2017 |
| 2017: обновление с 2015 или новая установка | 2013, обновление 5 | 2013, обновление 5 |
| 2017: обновление с 2015 или новая установка | 2013, обновление 5 | 2013, обновление 5 |
| 2015: обновление с 2013 | 2013 |2013 |
| 2015: новая установка | 2013 | 2013 |
| 2015: обновление с 2013 или новая установка | 2013 | 2013 |
| 2013 | 2013 | 2013 |
::: moniker-end

> [!NOTE]
> Сценарии Lab Management в TFS 2018 и Azure DevOps Services являются устаревшими. Дополнительные сведения см. в статье [Заметки о выпуске TFS 2018](/visualstudio/releasenotes/tfs2018-relnotes#--removing-support-for-lab-center-and-automated-testing-flows-in-microsoft-test-manager).

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Обновление агентов тестирования Visual Studio 2013

Рекомендуем использовать агенты для Visual Studio во всех сценариях нового автоматического тестирования. Вы можете использовать задачу *Deploy Test Agents* (Развертывание агентов тестирования) в конвейере сборки, чтобы скачать и установить агенты тестирования на компьютере.

В следующей таблице описаны сценарии, поддерживаемые инструментарием "Agents для Visual Studio 2013" и альтернативными решениями для Team Foundation Server (TFS) 2015 и Azure Test Plans:

| Сценарии, поддерживаемые Agents для Visual Studio 2013 | Альтернатива в TFS и Azure Test Plans |
| - | - |
| Рабочий процесс "сборка-развертывание-тестирование" в Visual Studio | Пользователи могут использовать [конвейер сборки](/azure/devops/pipelines/index?view=vsts&preserve-view=true) (не сборку XAML) для сценариев сборки, развертывания и тестирования в TFS. |
| Нагрузочные тесты (тестирование производительности) с использованием удаленных локальных компьютеров | Используйте обновление 5 для контроллеров и агентов тестирования 2013 для локального выполнения нагрузочных тестов. |
| Удаленное выполнение автоматических тестов из Microsoft Test Manager (не рекомендуется в Visual Studio 2017) с использованием лабораторной среды | Сейчас альтернативы этому сценарию не существует. Мы рекомендуем использовать задачу "Запуск функциональных тестов" в определениях сборок и выпусков (не в сборке XAML) для удаленного выполнения тестов. |
| Разработчики, выполняющие удаленные тесты в Visual Studio | Больше не поддерживается. |
