---
title: Начальная страница Snapshot Debugger
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf2aba33089623dc98a90c23166291bb2d6e7123
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905280"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>Начало работы со Snapshot Debugger

Теперь Visual Studio Snapshot Debugger подключен к службе, и вы можете начать сбор моментальных снимков, чтобы упростить отладку.

Чтобы использовать Snapshot Debugger, задайте точки моментальных снимков в коде, нажмите кнопку, чтобы начать сбор моментальных снимков, а затем запустите сценарий. При выполнении кода, в котором установлена точка моментальных снимков, создается моментальный снимок приложения. Чтобы открыть моментальный снимок, щелкните его в Visual Studio в окне Средств диагностики. После этого можно отлаживать моментальный снимок в службе так, как будто он локальный. Подробные инструкции приведены далее.

## <a name="collect-and-view-snapshots"></a>Сбор и просмотр моментальных снимков

Snapshot Debugger собирает моментальные снимки из приложения. Моментальные снимки — это снимки приложения на определенный момент времени. Вы указываете Visual Studio, когда и где следует получить моментальный снимок, устанавливая точку моментальных снимков в коде. В точке моментальных снимков задаются все необходимые условия для получения моментального снимка изучаемой проблемы.

### <a name="set-a-snappoint"></a>Настройка точки моментальных снимков

1. В редакторе кода щелкните левое внутреннее окно рядом с интересующей вас строкой кода, чтобы задать точку моментальных снимков. Убедитесь в том, что будет выполняться именно этот код.

    ![Задание точки моментальных снимков в редакторе](../media/snapshot-startpage-set-snappoint.png)

    В левом поле, в том месте, где вы щелкнули мышью, появляется сиреневый шестиугольник.

2. Нажмите кнопку **Запустить коллекцию**, чтобы включить точку моментальных снимков.

### <a name="open-a-snapshot"></a>Открытие моментального снимка

1. При выполнении точки моментальных снимков в окне "Средства диагностики" справа появляется снимок. Если это окно не открывается, последовательно выберите **Отладка** > **Окна** > **Показать средства диагностики**.

    ![Моментальный снимок в окне Средств диагностики](../media/snapshot-startpage-diagsession-window.png)

2. Чтобы открыть моментальный снимок, дважды щелкните его.

### <a name="inspect-snapshot-data"></a>Проверка данных моментальных снимков

В этом представлении вы можете наводить указатель на переменные для просмотра советов, использовать окна "Локальные переменные", "Контрольные значения" и "Стек вызовов", а также вычислять выражения.

Сам веб-сайт является активным, и это не влияет на конечных пользователей. По умолчанию создается только один моментальный снимок для каждой точки моментальных снимков. После создания моментального снимка точка моментальных снимков отключается. Если вы хотите сделать еще один снимок в одной точке, вы можете снова включить ее, нажав **Обновить коллекцию**.

### <a name="set-a-logpoint"></a>Задание точки ведения журнала

1. Щелкните правой кнопкой мыши значок точки моментальных снимков (сиреневый шестиугольник) и выберите пункт **Параметры**.

2. В окне **Параметры точки моментальных снимков** выберите элемент **Действия**.

    ![Условия точки моментальных снимков](../media/snapshot-startpage-logpoint.png)

3. В поле **Сообщение** введите сообщение журнала, которое хотите зарегистрировать. Вы также можете оценить переменные в сообщении журнала, поместив их в фигурные скобки.

    Если выбрать вариант **Отправить в окно вывода**, при достижении точки ведения журнала сообщение отображается в окне "Средства диагностики".

    Если выбрать вариант **Отправить в журнал приложений**, при достижении точки ведения журнала сообщение отображается в любом месте, где его можно просмотреть в `System.Diagnostics.Trace` (или `ILogger` в .NET Core), например в App Insights.

## <a name="learn-more"></a>Дополнительные сведения

Дополнительные сведения о Snapshot Debugger см. на [странице документации](../debug-live-azure-applications.md). Узнайте больше о настройке условий для упрощения поиска ошибок.

## <a name="dont-show-me-this-again"></a>Больше не показывать

Чтобы больше начальная страница Snapshot Debugger больше не отображалась при подключении Snapshot Debugger, измените параметр **Показывать страницу "Приступая к работе" при запуске сеанса** на странице **Сервис** > **Параметры** > **Snapshot Debugger**.

![Страница параметров Snapshot Debugger](../media/snapshot-startpage-tools-options.png)
