---
title: Использование Emulator Express для запуска и отладки облачной службы Azure на локальном компьютере | Документация Майкрософт
description: Использование Emulator Express для запуска и отладки облачной службы на локальном компьютере
author: mikejo5000
manager: jillfra
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 89d6662a1da987f927951937d04426b5e0b8cfa9
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846582"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Использование Emulator Express для запуска и отладки облачной службы Azure на локальном компьютере
Emulator Express позволяет протестировать и отладить облачную службу, не запуская Visual Studio от имени администратора. В зависимости от требований облачной службы параметры проекта можно задать таким образом, чтобы использовался либо Emulator Express, либо полный эмулятор. Дополнительные сведения о полном эмуляторе см. в статье [Запуск приложения Azure в эмуляторе вычислений](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Использование Emulator Express в Visual Studio
При создании проекта Azure в пакете Azure SDK 2.3 или более поздней версии Emulator Express используется автоматически. Для существующих проектов, созданных с использованием более ранней версии пакета Azure SDK, выбрать Emulator Express позволяет выполнение описанных ниже действий.

1. Создайте или откройте проект облачной службы Azure в среде Visual Studio.

1. В **обозревателе решений** щелкните проект правой кнопкой мыши и в контекстном меню выберите пункт **Свойства**.

1. На странице свойств проекта выберите вкладку **Веб**.

    ![Свойства проекта облачной службы Azure](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. В разделе **Локальный сервер Development Server** выберите **Использовать IIS Express**.

1. В разделе **Эмулятор** выберите **Использовать Emulator Express**.
   
1. Чтобы запустить Emulator Express, выполните следующую команду в командной строке: 

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Ограничения Emulator Express
Ниже перечислены известные ограничения Emulator Express. 

- Emulator Express несовместим с веб-сервером IIS.
- Облачная служба может содержать несколько ролей, однако каждая роль ограничивается одним экземпляром.
- Невозможен доступ к портам с номерами меньше 1000. Это значит, что если ваш поставщик проверки подлинности обычно использует порт с номером меньше 1000, то вам придется изменить его на порт с номером больше 1000.
- Все ограничения, связанные с эмулятором вычислений Azure, применяются также к Emulator Express. Например, число экземпляров роли в развернутой службе не может быть больше 50. Дополнительные сведения об эмуляторе вычислений Azure см. в статье [Запуск приложения Azure в эмуляторе вычислений](https://docs.microsoft.com/visualstudio/azure/vs-azure-tools-performance-profiling-cloud-services?view=vs-2019).

## <a name="next-steps"></a>Следующие шаги
[Отладка облачных служб Azure](vs-azure-tools-debugging-cloud-services-overview.md)
