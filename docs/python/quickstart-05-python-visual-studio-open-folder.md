---
title: Краткое руководство. Открытие папки с кодом Python
description: В этом кратком руководстве описано, как открыть и выполнить папку с кодом Python без использования проекта Visual Studio (только для Visual Studio 2019).
ms.date: 03/12/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
monikerRange: '>= vs-2019'
ms.openlocfilehash: ab234d9482cf9cbab49c15167ea45aff9ac2c7e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431158"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>Краткое руководство. Открытие и выполнение кода Python в папке

[Установив поддержку Python в Visual Studio 2019](installing-python-support-in-visual-studio.md), вы сможете легко перенести существующий код Python в Visual Studio 2019 без необходимости создавать проект Visual Studio.

> [!Note]
> В Visual Studio 2017 и более ранних версиях для выполнения кода Python нужно всегда создавать проект Visual Studio, что можно легко сделать с помощью встроенного шаблона проекта. Подробнее см. в [кратком руководстве по созданию проекта Python на основе существующего кода](quickstart-01-python-in-visual-studio-project-from-existing-code.md).

1. В этом пошаговом руководстве описано, как использовать любую папку с кодом Python. Чтобы в точности повторить все действия из описанного ниже примера, клонируйте репозиторий GitHub gregmalcolm/python_koans на локальный компьютер, выполнив команду `git clone https://github.com/gregmalcolm/python_koans` в соответствующей папке.

1. Запустите Visual Studio 2019 и в начальном окне выберите **Открыть** в нижней части столбца **Приступить к работе**. Если вы уже запустили Visual Studio, просто выберите **Файл** > **Открыть** > **Папка**.

    ![Экран запуска Visual Studio](media/quickstart-open-folder/01-open-local-folder.png)

1. Перейдите к папке с кодом Python и щелкните **Выбрать папку**. Если вы используете код python_koans, не забудьте выбрать папку `python3` в клонированной папке.

    ![Диалоговое окно "Выбор папки", которое открывается командой "Открыть папку"](media/quickstart-open-folder/02-select-folder.png)

1. Visual Studio отображает папку в **обозревателе решений** в виде **представления папки**. Здесь вы можете разворачивать и сворачивать папки с помощью стрелок в левой части имени папки:

    ![Элементы управления для развертывания и свертывания папок в обозревателе решений](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. Когда вы открываете папку Python, Visual Studio создает несколько скрытых папок для управления параметрами, связанными с проектом. Чтобы увидеть эти папки (и любые другие скрытые файлы и папки, например папку *.git*), нажмите кнопку **Показать все файлы** на панели инструментов:

    ![Просмотр скрытых папок в обозревателе решений](media/quickstart-open-folder/05-view-hidden-folders.png)

1. Чтобы запустить код, определите файл запуска (основной файл программы). В нашем примере используется файл запуска *contemplate-koans.py*. Щелкните этот файл правой кнопкой мыши и выберите пункт **Задать как файл запуска**.

    ![Настройка элемента запуска в обозревателе решений](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > Если выбранный элемент запуска не находится в открытой корневой папке, добавьте в JSON-файл конфигурации запуска строку, как описано в разделе о [настройке рабочего каталога](#set-a-working-directory).

1. Запустите код, нажав клавиши **CTRL**+**F5** или выбрав **Отладка** > **Запуск без отладки**. Вы также можете нажать на панели инструментов кнопку, на которой изображен символ воспроизведения. Эта кнопка запускает код в отладчике Visual Studio. Во всех случаях Visual Studio обнаружит, что выбранный элемент запуска является файлом Python, и автоматически выполнит код в окружении Python по умолчанию. (Это окружение отображается справа от элемента запуска на панели инструментов.)

    ![Кнопка запуска отладчика на панели инструментов](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. Выходные данные программы отображаются в отдельном командном окне:

    ![Окно вывода для выполняемого кода Python](media/quickstart-open-folder/08-result-window.png)

1. Чтобы выполнить код в другом окружении, выберите нужное окружение из раскрывающегося списка на панели инструментов, а затем снова запустите элемент запуска.

1. Чтобы закрыть папку в Visual Studio, выберите в меню команду **Файл** > **Закрыть папку**.

## <a name="set-a-working-directory"></a>Настройка рабочего каталога

По умолчанию Visual Studio выполняет проекты Python, открытые в виде папки, в корне этой самой папки. Но код вашего проекта может ожидать, что Python выполняется во вложенной папке. Предположим, что вы открыли корневую папку репозитория python_koans и выбрали в качестве элемента запуска файл *python3/contemplate-koans.py*. Если вы теперь выполните код, появится сообщение о том, что не удается найти файл *koans.txt*. Эта ошибка связана с тем, что *contemplate-koans.py* ожидает выполнение Python в папке *python3*, а не корневой папке репозитория.

В таком случае следует добавить в JSON-файл конфигурации запуска дополнительную строку, которая указывает рабочий каталог:

1. Щелкните правой кнопкой мыши файл запуска Python (*.py*) в **обозревателе решений** и выберите **Параметры отладки и запуска**.

    ![Команда "Параметры отладки и запуска" для файла Python](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. В открывшемся диалоговом окне **Запуск отладчика** выберите вариант **По умолчанию** и щелкните **Выбрать**.

    ![Команда "Параметры отладки и запуска" для файла Python](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > Если вы не видите здесь вариант **По умолчанию**, убедитесь, что при выборе команды **Параметры отладки и запуска** вы щелкнули правой кнопкой мыши именно файл Python с расширением *.py*. Visual Studio использует тип файла для выбора отображаемых вариантов действий в отладчике.

1. Visual Studio откроет файл с именем *launch.vs.json*, расположенный в скрытой папке *.vs*. Этот файл описывает контекст отладки для проекта. Чтобы указать рабочую папку, добавьте значение для параметра `"workingDirectory"`, как в `"workingDirectory": "python3"` для примера python-koans:

    ```json
    {
      "version": "0.2.1",
      "defaults": {},
      "configurations": [
        {
          "type": "python",
          "interpreter": "(default)",
          "interpreterArguments": "",
          "scriptArguments": "",
          "env": {},
          "nativeDebug": false,
          "webBrowserUrl": "",
          "project": "python3\\contemplate_koans.py",
          "name": "contemplate_koans.py",
          "workingDirectory": "python3"
        }
      ]
    }
    ```

1. Сохраните файл и снова запустите программу. Теперь она выполняется в указанной папке.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Учебник. Работа с Python в Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>См. также

- [Краткое руководство. Создание проекта Python на основе существующего кода](quickstart-01-python-in-visual-studio-project-from-existing-code.md).
- [Краткое руководство. Создание проекта Python из репозитория](quickstart-03-python-in-visual-studio-project-from-repository.md).
- [Определение существующего интерпретатора Python вручную](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
