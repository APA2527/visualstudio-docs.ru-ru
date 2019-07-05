---
title: Практическое руководство. Добавление зависимости в пакет VSIX | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee6ebeb776e6aa85d5fba200ac357a7375fa2b99
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341049"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Практическое руководство. Добавление зависимости в пакет VSIX

Можно настроить развертывание пакета VSIX, который устанавливает все зависимости, которых еще нет на целевом компьютере. Для этого необходимо включить файл с зависимостями VSIX для *source.extension.vsixmanifest* файл.

## <a name="to-add-a-dependency"></a>Добавление зависимости

1. Откройте *source.extension.vsixmanifest* файл **разработки** представления. Перейдите к **зависимости** вкладку и нажмите кнопку **New**.

2. Чтобы добавить установленное расширение: в **добавить новую зависимость** выберите **установлено расширение** и затем для **имя**, выберите расширение в списке.

3. Чтобы добавить другой файл VSIX, который не установлен: в **добавить новую зависимость** выберите **файл в файловой системе** , а затем использовать **Обзор** кнопку, чтобы выбрать VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Требуется конкретный выпуск Visual Studio

Если расширение требует определенной версии Visual Studio 2017, например, это зависит от компонентов, выпущена в версии 15.3, можно указать номер сборки в VSIX **InstallationTarget**. Например выпуске 15.3 имеет ряд сборки "15.0.26730.3». Вы увидите сопоставление выпусков для номера сборки [здесь](../install/visual-studio-build-numbers-and-release-dates.md). Обратите внимание на то, что с помощью номер выпуска «15.3"не будет работать правильно.

Если для расширения требуется 15.3 или более поздней версии, можно объявить **InstallationTarget версии** как [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

Установщик VSIX обнаружит более ранних версиях Visual Studio и информировать пользователей о том, что более позднее обновление является обязательным.

## <a name="see-also"></a>См. также

- [Справочник по схеме 1.0 расширение VSIX](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Подготовка расширения для развертывания установщика Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
