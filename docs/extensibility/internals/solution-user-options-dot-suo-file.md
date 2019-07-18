---
title: Пользовательских параметров решения (. SUO-) файл | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e54f89b9f231e4ae18e200718a5cc25cb3f3ceb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322616"
---
# <a name="solution-user-options-suo-file"></a>Файл параметров пользователя решения (SUO-файл)
Решения (SUO-) в файле пользователя содержит параметры пользователя решения. Этот файл не следует проверять систему управления версиями.

 Решения (SUO-) в файле пользователя — это структурированное хранилище, или составным, файл, хранящийся в двоичном формате. Сохранить сведения о пользователе в потоки с имя потока, что ключ, который будет использоваться для определения сведений в SUO-файл. Файл пользовательских параметров решения используется для хранения настройки параметров пользователя, а также создается автоматически, когда Visual Studio сохраняет решение.

 Когда среде открывает файл SUO, он перечисляет всех загруженных пакетов VSPackage. Если VSPackage реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> интерфейс, то среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> метод VSPackage, попросите его для загрузки всех данных из SUO-файл.

 Это в пакете VSPackage обязан знать, что потоков, наверняка приходилось писать в SUO-файл. Для каждого потока, который он написал, VSPackage вызывает обратно в среду через <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> для загрузки конкретного потока, который определяется с помощью ключа, которое является именем потока. Среды затем осуществляет обратный вызов VSPackage для чтения этого конкретного потока, передав имя потока и `IStream` указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> метод.

 В этот момент другой вызов `LoadUserOptions` ли другой участок SUO-файл, имеющий для чтения. Этот процесс продолжается, пока все потоки данных в файл SUO были прочитаны и обрабатываются средой.

 При сохранении или закрытии, среда вызывает метод решения <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> метод с указателем на <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> метод. `IStream` Содержащий двоичные данные для сохранения передается <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> метод, который затем будет записывать данные в файл SUO и вызовы `SaveUserOptions` метод, чтобы выяснить, имеется другой поток данных для записи .suo файл.

 Эти два метода `SaveUserOptions` и `WriteUserOptions`, называются рекурсивно для каждого потока данных сохраняется в SUO-файл, передав указатель на `IVsSolutionPersistence`. Они называются рекурсивно, чтобы разрешить для записи нескольких потоков к SUO-файл. Таким образом сведения о пользователе сохраняется с помощью решения и гарантированно существует при следующем открытии решения.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Решения](../../extensibility/internals/solutions-overview.md)