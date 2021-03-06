---
title: Поиск потока в представлении потоков | Документация Майкрософт
description: Поиск конкретного потока в представлении потоков средства Spy++ с использованием идентификатора потока или строки модуля в качестве условия поиска в процессе отладки в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85d82897144a0ed366d95dfa590a09224a875f55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845065"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Практическое руководство. поиск потока в представлении потоков
Вы можете найти конкретный поток в представлении потоков, используя идентификатор потока или строку модуля в качестве условия поиска. Вы также можете указать начальное направление поиска. Поля в диалоговом окне будут содержать атрибуты потока, выбранного в дереве потока.

### <a name="to-search-for-a-thread-in-threads-view"></a>Для поиска потока в представлении потоков

1. Расположите окна так, чтобы были видны окно Spy++ и активное окно [Представление потоков](../debugger/threads-view.md).

2. В меню **Поиск** выберите **Найти поток**.

    Откроется диалоговое окно [Поиск потока](../debugger/thread-search-dialog-box.md).

3. В качестве условия поиска введите идентификатор потока или строку модуля.

4. Очистите все поля, в которых не нужно указывать значения.

   > [!TIP]
   > Чтобы найти все потоки, принадлежащие модулю, очистите текстовое поле **Поток** и введите имя модуля в поле **Модуль**. Затем используйте элемент **Найти далее**, чтобы продолжить поиск потоков.

5. Нажимайте кнопки **Вверх** или **Вниз**, чтобы выбрать начальное направление поиска.

6. Нажмите кнопку **ОК**.

   Если будет найдено подходящий поток, он выделяется в окне представления потоков.