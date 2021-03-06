---
title: Измерение производительности из командной строки
description: Измеряйте производительность ЦП и использование управляемой памяти в приложении из командной строки.
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, command-line
- Diagnostics Tools, command-line
- CPU Usage, command-line
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 0b1d5906213b148605e35c483b377280dc942515
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936552"
---
# <a name="measure-application-performance-from-the-command-line"></a>Измерение производительности приложения из командной строки

Сведения о производительности приложения можно собирать с помощью программы командной строки.

В примере, описанном в этой статье, вы можете собирать данные производительности для Блокнота (Майкрософт), но тот же метод можно использовать для профилирования любого процесса.

## <a name="prerequisites"></a>Предварительные требования

* Visual Studio 2019 или более поздние версии

* Знание программы командной строки

* Чтобы собрать сведения о производительности на удаленном компьютере без установки Visual Studio, установите на нем [инструменты удаленной отладки для Visual Studio](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019). Версия средств должна соответствовать версии Visual Studio.

## <a name="collect-performance-data"></a>Сбор данных производительности

Профилирование с помощью средств CLI диагностики Visual Studio осуществляется путем присоединения к процессу средства профилирования, а также одного из агентов-сборщиков. При подключении средства профилирования вы начинаете сеанс диагностики, который фиксирует и сохраняет данные профилирования, пока средство не будет остановлено, после чего эти данные экспортируются в файл *.diagsession*. Затем этот файл можно открыть в Visual Studio, чтобы проанализировать результаты.

1. Запустите Блокнот и откройте диспетчер задач, чтобы получить его идентификатор процесса (PID). В диспетчере задач найдите PID на вкладке **Сведения**.

1. Откройте командную строку и перейдите в каталог с исполняемым файлом агента сбора, обычно здесь (для Visual Studio Enterprise).

   ```<Visual Studio installation folder>\2019\Enterprise\Team Tools\DiagnosticsHub\Collector\```

1. Запустите *VSDiagnostics.exe*, введя следующую команду.

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Необходимо включить следующие аргументы:

   * \<*id*> — определяет сеанс сбора. Идентификатор должен быть числом от 1 до 255.
   * \<*pid*> — идентификатор процесса, для которого вы хотите выполнить профилирование. В данном случае это идентификатор процесса, найденный на шаге 1.
   * \<*configFile*> — файл конфигурации для агента сборки, который вы хотите запустить. Дополнительные сведения см. в разделе [Файлы конфигурации для агентов](#config_file).

   Например, можно использовать следующую команду для агента CPUUsageBase, заменив *pid*, как описано выше.

   ```cmd
   VSDiagnostics.exe start 1 /attach:<pid> /loadConfig:AgentConfigs\CPUUsageLow.json
   ```

1. Измените размер Блокнот или введите в него текст, чтобы собрать интересные данные профилирования.

1. Остановите сеанс сбора и отправьте выходные данные в файл, введя следующую команду.

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. Найдите выходной файл *.diagsession*, полученный в результате предыдущей команды, и откройте его в Visual Studio (**Файл** > **Открыть**), чтобы изучить собранные сведения.

   Для анализа результатов ознакомьтесь с документацией по соответствующему средству контроля производительности. Например, это может быть средство [Загрузка ЦП](../profiling/cpu-usage.md), [средство выделения объектов .NET](../profiling/dotnet-alloc-tool.md) или инструмент [База данных](../profiling/analyze-database.md).

## <a name="agent-configuration-files"></a><a name="config_file"></a> Файлы конфигурации агента

Агенты сборки являются взаимозаменяемыми компонентами, которые собирают различные типы данных в зависимости от того, что вы пытаетесь измерить.

Для удобства можно хранить эту информацию в файле конфигурации агента. Файл конфигурации — это файл *.json*, содержащий как минимум имя *.dll* и его CLSID COM. Вот пример файлов конфигурации, которые находятся в следующей папке:

```<Visual Studio installation folder>Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

Скачать и просмотреть файлы конфигурации агента можно по следующим ссылкам:

- https://aka.ms/vs/diaghub/agentconfig/cpubase
- https://aka.ms/vs/diaghub/agentconfig/cpuhigh
- https://aka.ms/vs/diaghub/agentconfig/cpulow
- https://aka.ms/vs/diaghub/agentconfig/database
- https://aka.ms/vs/diaghub/agentconfig/dotnetasyncbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetallocbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetalloclow
- https://aka.ms/vs/diaghub/agentconfig/dotnetcountersbase

Конфигурации CpuUsage (базовая/низкая/высокая), которые соответствуют данным, собранным для инструмента профилирования [Загрузка ЦП](../profiling/cpu-usage.md).
Конфигурации DotNetObjectAlloc (базовая/низкая), которые соответствуют данным, собранным для [инструмента выделения объектов .NET](../profiling/dotnet-alloc-tool.md).

Базовая/низкая/высокая конфигурации означают частоту выборки. Например, "Низкая" означает 100 выборок в секунду, а "Высокая" — 4000 выборок в секунду.

Чтобы средство *VSDiagnostics.exe* работало с агентом сборки, ему требуется DLL и CLSID COM для соответствующего агента, и у агента могут быть дополнительные параметры конфигурации. Если вы используете агент без файла конфигурации, используйте формат в следующей команде.

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>Разрешения

Чтобы выполнить профилирование приложения, которое требует повышенного уровня разрешений, используйте командную строку с повышенными привилегиями.
