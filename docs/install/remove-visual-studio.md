---
title: Удаление Visual Studio
titleSuffix: ''
description: Пошаговые инструкции по полному удалению Visual Studio с компьютера.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fec652e0089a8baae79b6fa9446249710ea2f40d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594517"
---
# <a name="remove-visual-studio"></a>Удаление Visual Studio

Если произошла неустранимая ошибка, из-за которой невозможно восстановить или удалить Visual Studio, вы можете запустить средство `InstallCleanup.exe`, чтобы удалить файлы установки и сведения о продукте для всех установленных экземпляров Visual Studio 2017 или Visual Studio 2019.

> [!WARNING]
> Используйте средство InstallCleanup **только в крайнем случае**, если не удается выполнить восстановление или удаление. Это средство может удалить функции из других установок Visual Studio или других продуктов, которые затем, возможно, потребуется восстановить или переустановить.

## <a name="run-installcleanupexe"></a>Запуск InstallCleanup.exe

Со средством `InstallCleanup.exe` можно использовать любой из следующих параметров командной строки:

| Параметр | Поведение |
| ------ | -------- |
| `-i`   | Этот параметр используется по умолчанию, если не переданы другие параметры. Он приводит к удалению только главного каталога установки и сведений о продукте. Используйте этот параметр, если после запуска средства `InstallCleanup.exe` вы планируете переустановить ту же версию Visual Studio. |
| `-f`   | Этот параметр приводит к удалению главного каталога установки, сведений о продукте и большинства других компонентов, которые установлены вне каталога установки и могут использоваться другими экземплярами Visual Studio или иными продуктами. Используйте этот параметр, если вы планируете удалить среду Visual Studio и не устанавливать ее повторно. |

Ниже описано, как запустить средство `InstallCleanup.exe`.

1. Закройте установщик Visual Studio.
1. Откройте командную строку от имени учетной записи администратора. Чтобы открыть командную строку с правами администратора, выполните указанные ниже действия.
   * Введите **cmd** в поле "Введите текст для поиска".
   * Щелкните правой кнопкой мыши пункт **Командная строка** и выберите команду **Запуск от имени администратора**.
1. Введите полный путь к средству `InstallCleanup.exe` и добавьте предпочитаемый параметр командной строки. По умолчанию путь средства выглядит следующим образом:

   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

   > [!NOTE]
   > Если вы не можете найти средство `InstallCleanup.exe` в каталоге Visual Studio Installer, который всегда находится в `%ProgramFiles(x86)%\Microsoft Visual Studio`, ниже описаны дальнейшие действия. Следуйте инструкциям для [установки Visual Studio](install-visual-studio.md). Затем, когда отобразится экран выбора рабочих нагрузок, закройте окно и снова выполните шаги, описанные на этой странице.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка Visual Studio](install-visual-studio.md)
* [Обновление Visual Studio](update-visual-studio.md)
* [Изменение Visual Studio](modify-visual-studio.md)
* [Удаление Visual Studio](uninstall-visual-studio.md)
