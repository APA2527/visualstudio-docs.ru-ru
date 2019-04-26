---
title: Задачи MSBuild, относящиеся к Visual C++ | Документация Майкрософт
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 243ed824ba278300a798a34b05854129e8197504
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004590"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Задачи MSBuild, относящиеся к Visual C++
Задачи содержат код, который выполняется в процессе сборки. После установки Visual C++ доступны следующие задачи, помимо тех, которые устанавливаются вместе с [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Дополнительные сведения см. в [обзоре MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp-overview).

 Помимо общих для всех задач параметров, у каждой задачи есть следующие параметры.

| Параметр | Описание |
|-------------------| - |
| `Condition` | Необязательный параметр `String` .<br /><br /> Выражение `Boolean`, на основании которого механизм [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] определяет, будет ли выполняться эта задача. Сведения о поддерживаемых в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] условиях см. в статье [об условиях MSBuild](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Необязательный параметр. Может содержать одно из следующих значений:<br /><br /> -   **WarnAndContinue** или **true**. При сбое одной задачи продолжается выполнение сборки и всех последующих задач в элементе [Target](../msbuild/target-element-msbuild.md), а все ошибки из задачи рассматриваются как предупреждения.<br />-   **ErrorAndContinue**. При сбое задачи последующие задачи в элементе `Target` и сборке продолжают выполняться, а все ошибки из задачи рассматриваются как ошибки.<br />-   **ErrorAndStop** или **false** (значение по умолчанию). При сбое задачи отменяется выполнение сборки и последующих задач в элементе `Target`, и фиксируется сбой для выполнения элемента `Target` и всей сборки.<br /><br /> Версии платформы .NET Framework, предшествовавшие 4.5, поддерживали только значения `true` и `false`.<br /><br /> Дополнительные сведения см. в разделе [Как Игнорирование ошибок в задачах](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Задача BscMake](../msbuild/bscmake-task.md)|Заключает в оболочку средство "Программа управления сведениями о просмотре Майкрософт" (*bscmake.exe*).|
|[Задача CL](../msbuild/cl-task.md)|Использует оболочку компилятора Visual C++ (*cl.exe*).|
|[Задача CPPClean](../msbuild/cppclean-task.md)|Удаляет временные файлы, которые MSBuild создает при сборке проекта Visual C++.|
|[Задача ClangCompile](../msbuild/clangcompile-task.md)|Создает программу-оболочку для компилятора Visual C++ (*clang.exe*).|
|[Задача CustomBuild](../msbuild/custombuild-task.md)|Создает программу-оболочку для компилятора Visual C++ (*cmd.exe*).|
|[Задача FXC](../msbuild/fxc-task.md)|Позволяет применять компиляторы шейдеров HLSL в процессе сборки.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Считывает старые журналы отслеживания, записывает новые журналы отслеживания и возвращает набор неактуальных элементов (задача вспомогательного приложения).|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Извлекает имя выходного файла для cl и других средств, которые позволяют указывать только выходной каталог или полное имя файла (задача вспомогательного приложения).|
|[Задача LIB](../msbuild/lib-task.md)|Заключает в оболочку 32-разрядный диспетчер библиотек Майкрософт (*lib.exe*).|
|[Задача Link](../msbuild/link-task.md)|Создает оболочку для компоновщика Visual C++ (*link.exe*).|
|[Задача MIDL](../msbuild/midl-task.md)|Является оболочкой для компилятора с языка MIDL (*midl.exe*).|
|[Задача MT](../msbuild/mt-task.md)|Является оболочкой для инструмента манифеста Майкрософт (*mt.exe*).|
|[Задача MultiToolTask](../msbuild/multitooltask-task.md)|Нет описания.|
|[Задача ParallelCustomBuild](../msbuild/parallelcustombuild-task.md)|Выполняет параллельные экземпляры [задачи CustomBuild](../msbuild/custombuild-task.md).|
|[Задача RC](../msbuild/rc-task.md)|Является оболочкой для средства компиляции ресурсов Microsoft Windows (*rc.exe*).|
|[Задача SetEnv](../msbuild/setenv-task.md)|Задает или удаляет значение указанной переменной среды.|
|[Базовый класс TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)|Наследует от класса [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[Задача VCMessage](../msbuild/vcmessage-task.md)|Заносит в журнал предупреждения и сообщения об ошибках, возникшие при сборке. (Не расширяется. Только для внутреннего использования.)|
|[Базовый класс VCToolTask](../msbuild/vctooltask-base-class.md)|Наследует от класса [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask).|
|[Задача XDCMake](../msbuild/xdcmake-task.md)|Является оболочкой для средства XML-документации (*xdcmake.exe*), которая помещает в XML-файл файлы комментариев (*XDC-файлы*) для файла *XML*.|
|[Задача XSD](../msbuild/xsd-task.md)|Создает оболочку для инструмента определения схемы XML (*xsd.exe*), который создает файлы схемы или класса из источника. *См. примечание ниже.*|
|[Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)|Описывает элементы системы MSBuild.|
|[Задачи](../msbuild/msbuild-tasks.md)|Описывает задачи, представляющие собой блоки кода, которые можно объединять для выполнения сборки.|
|[Написание задач](../msbuild/task-writing.md)|Создание задачи.|

> [!NOTE]
> Начиная с версии Visual Studio 2017 поддержка проектов C++ для *xsd.exe* отмечена как нерекомендуемая. Вы можете продолжать использовать API **Microsoft.VisualC.CppCodeProvider**, вручную добавив *CppCodeProvider.dll* в глобальный кэш сборок.