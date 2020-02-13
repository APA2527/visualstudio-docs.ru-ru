---
title: Действия при сборке
description: В этой статье описываются различные действия сборки, которые могут использоваться для проектов C#
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d55ab6aea15dbad7f1cbd718136fba261dfa1c69
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74983257"
---
# <a name="build-actions"></a>Действия при сборке

Все файлы в проекте Visual Studio для Mac имеют действие при сборке. Оно определяет, что происходит с файлом во время сборки. Его можно настроить, щелкнув правой кнопкой мыши любой файл и выбрав **Действие при сборке**, как показано ниже.

![Выбор действия сборки Compile в обозревателе решений](media/projects-and-solutions-image1.png)

Ниже приведены некоторые распространенные действия при сборке для проектов C#:

* **None** — файл не является частью сборки, он включен в проект для упрощения доступа из интегрированной среды разработки.
* **Compile** — файл будет передан компилятору C# в виде файла кода.
* **EmbeddedResource** — файл будет передан компилятору C# в виде ресурса, внедряемого в сборку. После этого можно использовать [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream) из пространства имен `System.Reflection` для чтения файла из сборки.
* **Content** — для проектов ASP.NET эти файлы будут включены в состав сайта при его развертывании. Для проектов Xamarin.iOS и Xamarin.Mac они будут включены в пакет приложений.

Можно выбрать несколько файлов в обозревателе решений, чтобы задать действие при сборке сразу для большого числа файлов.

Кроме того, существуют действия при сборке для конкретных проектов. Проекты Xamarin.iOS имеют действие при сборке **BundleResource**, которое добавляет файл как часть пакета приложений. Сведения о действиях при сборке для Xamarin.Android см. в руководстве по [процессу сборки](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).

## <a name="see-also"></a>См. также

- [Действия сборки (Visual Studio в Windows)](/visualstudio/ide/build-actions)