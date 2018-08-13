---
title: Создание приложения Node.js и React
description: В этом учебнике вы создадите приложение с помощью инструментов Node.js для Visual Studio.
ms.custom: mvc
ms.date: 05/23/2018
ms.technology: vs-nodejs
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f7bb4dfea8e23941e6d9ad29b9760c9e7c85fc5f
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39567146"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Учебник. Создание приложения Node.js и React в Visual Studio

В Visual Studio можно легко создать проект Node.js и использовать IntelliSense и другие встроенные функции, поддерживающие Node.js. В этом учебнике по Visual Studio вы создадите проект веб-приложения Node.js на основе шаблона Visual Studio. Затем вы создадите простое приложение с помощью React.

В этом руководстве вы узнаете, как:
> [!div class="checklist"]
> * Создание проекта Node.js
> * Добавление пакетов npm
> * Добавление кода React в приложение
> * Транскомпиляция JSX
> * Подключение отладчика

## <a name="prerequisites"></a>Предварительные требования

* У вас должна быть установлена среда Visual Studio 2017 и должна иметься рабочая нагрузка "Разработка Node.js".

    Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), если еще не сделали этого.

    Если вам нужно установить рабочую нагрузку, но среда Visual Studio уже имеется, щелкните ссылку **Открыть Visual Studio Installer** в левой области диалогового окна **Новый проект**. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Разработка Node.js**, а затем элемент **Изменить**.

* У вас должна быть установлена среда выполнения Node.js.

    Этот учебник был протестирован с версией 8.11.2.

    Если она не установлена, установите версию LTS с веб-сайта [Node.js](https://nodejs.org/en/download/). Как правило, Visual Studio автоматически обнаруживает установленную среду выполнения Node.js. Если установленная среда выполнения не обнаружена, вы можете настроить проект так, чтобы он ссылался на установленную среду выполнения, на странице свойств (после создания проекта щелкните его узел правой кнопкой мыши и выберите пункт **Свойства**).

## <a name="create-a-project"></a>Создание проекта

Сначала создайте проект веб-приложения Node.js.

1. Откройте Visual Studio 2017.

1. В верхней строке меню выберите **Файл** > **Создать** > **Проект**.

1. В левой области диалогового окна **Новый проект** разверните узел **JavaScript** и выберите **Node.js**. В средней области выберите **Пустое веб-приложение Node.js**, введите **NodejsWebAppBlank** и нажмите кнопку **ОК**.

     Если шаблон проекта **Пустое веб-приложение Node.js** отсутствует, необходимо сначала установить рабочую нагрузку "Разработка Node.js".

    Visual Studio создаст решение и откроет проект.

    ![Проект Node.js в обозревателе решений](../javascript/media/tutorial-nodejs-react-project-structure.png)

    * Полужирным шрифтом выделен ваш проект, имя которого вы указали в окне **Новый проект**. В файловой системе этот проект представлен файлом *NJSPROJ* в папке проекта. Вы можете задать свойства и переменные среды, связанные с проектом, щелкнув его правой кнопкой мыши и выбрав пункт **Свойства**. Вы можете одновременно использовать и другие средства разработки, так как файл проекта не вносит изменения в источник проекта Node.js.

    * На верхнем уровне находится решение, имя которого по умолчанию совпадает с именем проекта. Решение, представленное на диске файлом *SLN*, является контейнером для одного или нескольких связанных проектов.

    * В узле npm представлены все установленные пакеты npm. Вы можете щелкнуть узел npm правой кнопкой мыши, чтобы найти и установить пакеты npm с помощью диалогового окна.

    * Файлы проекта, такие как *server.js*, отображаются в узле проекта. *server.js* — это запускаемый файл проекта.

## <a name="add-npm-packages"></a>Добавление пакетов npm

Для правильной работы приложения требуется ряд модулей npm.

* react
* react-dom
* express
* путем
* ts-loader
* typescript
* webpack
* webpack-cli

1. В обозревателе решений (правая область) щелкните правой кнопкой мыши узел **npm** в проекте и выберите пункт **Установить новые пакеты npm**.

    В диалоговом окне **Установка новых пакетов npm** можно выбрать для установки последнюю версию пакетов или указать версию. Если вы выбрали для установки текущую версию пакетов, но в дальнейшем возникают непредвиденные ошибки, может потребоваться установить определенные версии пакетов, которые указаны далее в этой статье.

1. В диалоговом окне **Установка новых пакетов npm** выполните поиск пакета react и щелкните **Установить пакет**, чтобы установить его.

    ![Установка пакетов npm](../javascript/media/tutorial-nodejs-react-install-packages.png)

    Выберите окно **Вывод**, чтобы увидеть ход установки пакета (выберите **npm** в поле **Показать выходные данные из**). После установки пакет появляется в узле **npm**.

    Файл *package.json* обновляется с использованием сведений о новых пакетах, включая их версию.

1. Вместо поочередного поиска и добавления остальных пакетов в пользовательском интерфейсе вставьте в файл package.json приведенный ниже код. Для этого замените раздел `dependencies` следующим кодом:

    ```js
    "dependencies": {
      "express": "4.16.2",
      "path": "0.12.7",
      "react": "16.4.0",
      "react-dom": "16.4.0",
      "ts-loader": "4.0.1",
      "typescript": "2.7.2",
      "webpack": "4.1.1",
      "webpack-cli": "2.0.11"
    }
    ```

    Если раздел `dependencies` отсутствует в версии пустого шаблона, необходимо добавить его вместо замены существующего раздела.

1. Щелкните правой кнопкой мыши узел **npm** в проекте и выберите команду **Обновить пакеты npm**.

    В области внизу выберите окно **Вывод**, чтобы увидеть ход установки пакетов. Установка может занять несколько минут. Чтобы увидеть выходные данные, выберите **Npm** в поле **Показать выходные данные из** в окне **Вывод**.

    Ниже показаны модули npm, отображаемые в обозревателе решений после установки.

    ![Пакеты npm](../javascript/media/tutorial-nodejs-react-npm-modules.png)

    > [!NOTE]
    > Чтобы установить пакеты npm из командной строки, щелкните узел проекта правой кнопкой мыши и выберите пункт **Открыть командную строку здесь**. Используйте стандартные команды Node.js для установки пакетов.

## <a name="add-project-files"></a>Добавление файлов проекта

В рамках этой процедуры вы добавите в проект четыре новых файла.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Для этого простого приложения новые файлы проекта добавляются в корень проекта. (В большинстве приложений файлы, как правило, добавляются во вложенные папки, после чего ссылки в виде относительных путей изменяются соответствующим образом.)

1. В обозревателе решений щелкните правой кнопкой мыши проект **NodejsWebAppBlank** и выберите пункт **Добавить** > **Новый элемент**.

1. В диалоговом окне **Добавление нового элемента** выберите **JSX-файл TypeScript**, введите имя файла *app.tsx* и нажмите кнопку **ОК**.

1. Повторите эти действия, чтобы добавить файл *webpack-config.js*. Вместо файла TypeScript JSX выберите **файл JavaScript**.

1. Выполните эти же действия, чтобы добавить файл *index.html* в проект. Вместо файла JavaScript выберите **HTML-файл**.

1. Выполните эти же действия, чтобы добавить файл *tsconfig.json* в проект. Вместо файла JavaScript выберите **Файл конфигурации TypeScript JSON**.

## <a name="add-app-code"></a>Добавление кода приложения

1. Откройте файл *server.js* и замените его содержимое следующим кодом:

    ```javascript
    'use strict';
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   В приведенном выше коде используется Express для запуска Node.js в качестве сервера веб-приложения. Этот код задает в качестве номера порта номер, настроенный в свойствах проекта (по умолчанию в свойствах настроен порт 1337). Чтобы открыть свойства проекта, в обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Свойства**.

1. Откройте файл *app.tsx* и добавьте следующий код:

    ```javascript
    declare var require: any

    var React = require('react');
    var ReactDOM = require('react-dom');

    class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    В приведенном выше коде используется синтаксис JSX и React для вывода простого сообщения.

1. Откройте файл *index.html* и замените раздел **body** на следующий код:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Эта HTML-страница загружает файл *app-bundle.js*, который содержит код JSX и React, транскомпилированный в обычный код JavaScript. Пока файл *app-bundle.js* пуст. В следующем разделе вы настроите параметры для транскомпиляции кода.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Настройка параметров компилятора webpack и TypeScript

В предыдущих шагах вы добавили файл *webpack-config.js* в проект. Далее вы добавите код конфигурации webpack. Вы добавите простую конфигурацию webpack, в которой указываются входной файл (*app.tsx*) и выходной файл (*app-bundle.js*) для объединения и транскомпиляции кода JSX в обычный код JavaScript. Для транскомпиляции также настраиваются некоторые параметры компилятора TypeScript. Этот код представляет собой базовую конфигурацию, которая служит для ознакомления с работой webpack и компилятора TypeScript.

1. В обозревателе решений откройте файл *webpack-config.js* и добавьте приведенный ниже код.

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    Код конфигурации webpack предписывает средству Webpack использовать загрузчик TypeScript для транскомпиляции JSX.

1. Откройте файл *tsconfig.json* и замените код по умолчанию следующим кодом, который задает параметры компилятора TypeScript:

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    В качестве исходного файла указывается файл *app.tsx*.

## <a name="transpile-the-jsx"></a>Транскомпиляция JSX

1. В обозревателе решений щелкните узел проекта правой кнопкой мыши и выберите пункт **Открыть командную строку здесь**.

1. В командной строке введите следующую команду:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    В окне командной строки будут выведены результаты.

    ![Запуск webpack](../javascript/media/tutorial-nodejs-react-run-webpack.png)

    Если вместо приведенных выше выходных данных будут выведены ошибки, их необходимо будет устранить, чтобы приложение работало. Если ваши версии пакетов npm отличаются от используемых в этом учебнике, это может быть причиной ошибок. Один из способов устранить ошибки — использовать именно те версии, которые показаны в предыдущих шагах. Кроме того, если одна или несколько из этих версий пакетов стали нерекомендуемыми, из-за чего возникают ошибки, может потребоваться установить более поздние версии.

1. В обозревателе решений щелкните правой кнопкой мыши узел проекта и выберите пункты **Добавить** > **Существующая папка**, а затем папку *dist* и щелкните **Выбрать папку**.

    Среда Visual Studio добавит в проект папку *dist*, которая содержит файлы *app-bundle.js* и *app-bundle.js.map*.

1. Откройте файл *app-bundle.js*, чтобы просмотреть транскомпилированный код JavaScript.

1. Если будет предложено перезагрузить файлы, которые были изменены в других средствах, выберите вариант **Да, для всех**.

    ![Загрузка измененных файлов](../javascript/media/tutorial-nodejs-react-reload-files.png)

Каждый раз при внесении изменений в файл *app.tsx* необходимо повторно выполнять команду webpack.

## <a name="run-the-app"></a>Запуск приложения

1. Убедитесь в том, что в качестве текущего целевого объекта отладки выбран Chrome.

    ![Выбор Chrome в качестве целевого объекта отладки](../javascript/media/tutorial-nodejs-react-debug-target.png)

1. Чтобы запустить приложение, нажмите клавишу **F5** (**Отладка** > **Начать отладку**) или кнопку с зеленой стрелкой.

    Откроется окно консоли Node.js, в котором показан порт, через который отладчик ожидает передачи данных.

    Visual Studio запускает приложение с помощью файла запуска *server.js*.

    ![Запуск React в браузере](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Закройте окно браузера.

1. Закройте окно консоли.

## <a name="set-a-breakpoint-and-run-the-app"></a>Установите точку останова и запустите приложение.

1. В файле *server.js* щелкните в поле слева от объявления `staticPath`, чтобы установить точку останова:

    ![Задание точки останова](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Точки останова — это один из самых простых и важных компонентов надежной отладки. Точка останова указывает, где Visual Studio следует приостановить выполнение кода, чтобы вы могли проверить значения переменных или поведение памяти либо выполнение ветви кода.

1. Чтобы запустить приложение, нажмите клавишу **F5** (**Отладка** > **Начать отладку**).

    Выполнение отладчика прервется в установленной точке останова (текущий оператор выделяется желтым цветом). Теперь вы можете изучить состояние приложения, наводя указатель мыши на переменные в текущей области и используя окна отладчика, такие как **Локальные** и **Контрольные значения**.

1. Чтобы продолжить выполнение приложения, нажмите клавишу **F5**.

1. Если вы хотите использовать инструменты разработчика Chrome, нажмите клавишу **F12**. С их помощью можно изучить модель DOM и взаимодействовать с приложением с помощью консоли JavaScript.

1. Закройте веб-браузер и консоль.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Установка и срабатывание точки останова в коде React на стороне клиента

В предыдущем разделе вы подключили отладчик к коду Node.js на стороне сервера. Чтобы можно было подключить отладчик из Visual Studio и попадать в точки останова в коде React на стороне клиента, необходимо правильно настроить процесс. Ниже описывается один из способов.

1. Закройте все окна Chrome.

1. Щелкните правой кнопкой мыши кнопку **Пуск** Windows, выберите команду **Выполнить** и введите следующую команду:

    `chrome.exe --remote-debugging-port=9222`

    Chrome будет запущен в режиме отладки.

1. Перейдите в Visual Studio и установите точку останова в коде файла *app-bundle.js* в функции `render()`, как показано на рисунке ниже.

    ![Задание точки останова](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

1. Выбрав Chrome в качестве целевого объекта отладки в Visual Studio, нажмите клавиши **CTRL**+**F5** (**Отладка** > **Запуск без отладки**), чтобы запустить приложение в браузере.

    Приложение откроется в новой вкладке браузера.

1. Выберите **Отладка** > **Присоединение к процессу**.

1. В диалоговом окне **Присоединение к процессу** выберите в поле **Присоединить к** элемент **Код Webkit** и введите **chrome** в поле фильтра, чтобы отфильтровать результаты поиска.

1. Выберите процесс Chrome с соответствующим портом узла (1337 в этом примере) и нажмите кнопку **Присоединить**.

    ![Присоединение к процессу](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Определить, что отладчик присоединился правильно, можно по открытию проводника DOM и консоли JavaScript в Visual Studio. Эти средства отладки аналогичны инструментам разработчика Chrome и средствам разработчика F12 для Edge.

    > [!NOTE]
    > Если отладчик не присоединяется и появляется сообщение "Не удалось присоединиться к процессу. Операция недопустима в текущем состоянии", — перед запуском Chrome в режиме отладки закройте все экземпляры Chrome через диспетчер задач. Возможно, выполняются расширения Chrome и препятствуют переходу в режим полной отладки.

1. Так как код с точкой останова уже был выполнен, обновите страницу браузера, чтобы точка останова была достигнута еще раз.

    Когда отладчик приостановит выполнение, вы можете изучить состояние приложения, наводя указатель мыши на переменные и используя окна отладчика. Вы также можете выполнять пошаговую отладку кода (клавиши **F5**, **F10** и **F11**).

    Точка останова может быть достигнута в файле *app-bundle.js* или сопоставленном с ним месте в файле *app.tsx* в зависимости от среды и состояния браузера. В любом случае вы можете выполнять пошаговую отладку кода и просматривать переменные.

    * Если требуется приостановка выполнения кода в *app.tsx*, но вам не удается это сделать, используйте **присоединение к процессу**, чтобы подключить отладчик, как это описано в предыдущих этапах. Затем откройте динамически созданный файл *app.tsx* в обозревателе решений. Для этого откройте **Документы скриптов** > **app.tsx**, установите точку останова и обновите страницу в браузере (установите точку останова в строке кода, допускающей точки останова, например в операторе `return` или объявлении `var`).

        Либо, если необходимо прервать выполнение кода в файле *app.tsx*, но сделать это не удается, попробуйте использовать оператор `debugger;` в *app.tsx* или установите точки останова в инструментах разработчика Chrome.

    * Если требуется приостановка выполнения кода в файле *app-bundle.js*, но это сделать не удается, удалите файл соответствия источника *app-bundle.js.map*.

    > [!TIP]
    > После того как вы впервые присоединитесь к процессу с помощью этих инструкций, в дальнейшем можно присоединяться к нему в Visual Studio 2017 с помощью команды **Отладка** > **Повторно подключиться к процессу**.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Развертывание приложения в службе приложений Linux](../javascript/publish-nodejs-app-azure.md)