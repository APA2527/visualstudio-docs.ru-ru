---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: d7d4027c53f599b4a17d267d5ebf72eee1ed296b
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2021
ms.locfileid: "98535305"
---
### <a name="tooltaskextension-parameters"></a>Параметры ToolTaskExtension

Эта задача наследуется от класса <xref:Microsoft.Build.Tasks.ToolTaskExtension>, который наследуется от класса <xref:Microsoft.Build.Utilities.ToolTask>, который, в свою очередь, наследуется от класса <xref:Microsoft.Build.Utilities.Task>. Эта цепочка наследования добавляет несколько параметров в задачи, которые от них происходят.

В следующей таблице описываются параметры базовых классов:

| Параметр | Описание |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Необязательный параметр `bool`.<br /><br /> Если задано значение `true`, то задача передает **/Q** в командную строку *cmd.exe* и командная строка не копируется в stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Необязательный параметр массива `String`.<br /><br /> Массив определений переменных среды, разделенных точкой с запятой. Каждое определение должно содержать имя и значение переменной среды, разделенные знаком равенства. Эти переменные частично передаются в порожденный исполняемый файл, дополняя или выборочно переопределяя обычный блок среды. Например, `Variable1=Value1;Variable2=Value2`. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Необязательный выходной параметр `Int32`, доступный только для чтения.<br /><br /> Задает код выхода, предоставляемый выполняемой командой. Если задача зарегистрировала какие-либо ошибки, но процесс имеет код выхода 0 (успешное завершение), этот параметр имеет значение -1. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Необязательный параметр `bool`.<br /><br /> Если он имеет значение `true`, то все сообщения, полученные в стандартном потоке ошибок, регистрируются как ошибки. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Необязательный параметр `String`.<br /><br /> Степень важности, с которой текст из стандартного выходного потока следует регистрировать в журнале. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Необязательный параметр `String`.<br /><br /> Степень важности, с которой текст из стандартного выходного потока следует регистрировать в журнале. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Необязательный параметр `Int32`.<br /><br /> Задает промежуток времени в миллисекундах, после которого исполняемый файл задачи прекращается. Значение по умолчанию — `Int.MaxValue`. Оно указывает, что период ожидания отсутствует. Время ожидания в миллисекундах. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Необязательный параметр `string`.<br /><br /> Он может реализовываться в проектах для переопределения параметра ToolName. Задачи могут переопределять его для сохранения параметра ToolName. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Необязательный параметр `string`.<br /><br /> Указывает расположение, откуда задача загружает базовый исполняемый файл. Если этот параметр не задан, задача использует путь установки пакета SDK, соответствующий версии платформы, на которой выполняется MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Необязательный параметр `bool`.<br /><br /> Если задано значение `true`, эта задача создает пакетный файл для командной строки и выполняет его с помощью командного процессора вместо непосредственного выполнения команды. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Необязательный параметр `bool`.<br /><br /> Если задано значение `true`, эта задача создает узел при выполнении его задачи. |
