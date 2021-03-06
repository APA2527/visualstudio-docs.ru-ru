---
title: Анимация для Visual Studio | Документация Майкрософт
description: Сведения о правилах, позволяющих обеспечить единообразные и удобные для пользователя стили анимации в интегрированной среде разработки Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a7e8ea6514f29b99975b9e291d6a09ed2a0ad54e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934016"
---
# <a name="animations-for-visual-studio"></a>Анимация для Visual Studio
## <a name="animation-fundamentals"></a>Основы анимации

### <a name="animation-best-practices-in-visual-studio"></a>Рекомендации по анимации в Visual Studio
Следуйте этим правилам, чтобы обеспечить единообразные и удобные для пользователя стили анимации в интегрированной среде разработки Visual Studio.

- **Быть избирательным.** Ограничьте анимацию до тех, которые служат для конкретных целей.

- **Время и скорость важны** для обеспечения быстрого и естественного перехода:

  - Завершение анимированных переходов в течение одной половины секунды (500 миллисекунд).

  - Анимации, которые часто возникают, должны быть достаточно быстрыми, чтобы не прерывать рабочий процесс пользователя. Просмотрите анимацию в цикле и скорректируйте интервал времени, пока он не изменится правильно.

  - Анимация не должна быть настолько быстрой или жарринг, что ее сложно понять, но не настолько медленнее, что она делает один из них недостаточным для завершения перехода.

  - Используйте переменное время, чтобы подчеркнуть важность. Например, при переходе по последовательности элементов на диаграмме классов скорость перехода между элементами замедляется, чтобы сосредоточиться на важных элементах.

- **Используйте постепенную нелинейную замедление** от одного состояния к другому, предоставляя смысл приходом и естественного перемещения.

- По возможности **Используйте слабую анимацию при наведении указателя** мыши, чтобы обозначить Интерактивные элементы под мышью.

- Если вы сильно полагаетесь на анимацию в своих функциях, **Предоставьте возможность отключить их** локально (для всех функций) в качестве параметра в диалоговом окне " **Сервис > параметры** ".

- **Только одна анимация должна выполняться за раз** и передавать только один фрагмент информации. Несколько объектов, которые перемещают или пытаются передать несколько элементов, могут быть запутанными.

- **Тонкость важна.** В большинстве случаев анимация не требует вмешательства пользователя в целях обслуживания. Незначительные изменения в времени, последовательности и поведении могут значительно повлиять на восприятие, а также могут сделать разницу между эффективной и неэффективной анимацией.

- При использовании анимации, чтобы привлечь внимание к чему-то, **Убедитесь в том, что стоит прервать мысль пользователя**.

- **При отображении хода выполнения или состояния** через анимацию:

  - Перестает отображать перемещение хода выполнения, если базовый процесс не выполняется.

  - Отличить неопределенные процессы от процесса дезавершения процессов.

  - Убедитесь, что анимация содержит состояние завершения и сбоя.

  - Сократите использование анимации эффектов, отображающей состояние, и убедитесь, что они имеют реальное значение, предоставив дополнительные сведения о фактическом использовании. Примерами могут служить временные изменения состояния и экстренные колебания

#### <a name="animation-donts"></a>Запрет анимации:

- Не используйте небольшие перемещения (перемещение в небольшом объеме). Предпочитать плавность и изменения при перемещении объектов.

- Не используйте анимации, которые выполняются в большой области экрана. Независимо от размера этот стиль анимации отвлекается от пользователя.

- Не используйте анимацию, не связанную с объектом, к которому в данный момент привязан пользователь или который взаимодействует с.

- Не используйте анимацию, требующую вмешательства пользователя для сброса состояния, например, чтобы заставить пользователя реагировать на мигание уведомления, чтобы сделать его немигающим. Для их закрытия достаточно взаимодействия с ними.

Дополнительные сведения о приложениях для этих рекомендаций см. в разделе [шаблоны анимации](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Метрики анимации

- Система должна заметно реагировать на жесты пользователя менее чем на 10 миллисекунд.

- Выполнение анимированных переходов не должно занять больше 500 миллисекунд.

- Один из способов компенсировать переходы, требующие более длительного времени, — разделить ее на две части. Например, первая часть анимации может быть пустым контейнером содержимого (до 500 миллисекунд), за которым следует затухание содержимого в контейнере (до 500 миллисекунд).

- Для времени загрузки, которое можно вычислить, рекомендуется определить индикатор хода выполнения (индикатор выполнения "процент завершения").

- Для времени загрузки, которое не может быть вычислено, подходит индикатор занятости, такой как курсор или внедренная вращающаяся анимация (Загрузка или работающий индикатор).

### <a name="animation-as-communicator"></a>Анимация как Communicator
В пользовательском интерфейсе Visual Studio функция анимации работает только в качестве средства связи.  Он используется для передачи разнообразных сведений, например структурных изменений в пользовательском интерфейсе (например, когда меню открывается или закрывается). Анимация может помочь визуализировать зависящее от времени поведение сложных систем, таких как визуализация хода выполнения установки. Анимации также можно использовать для привлечения внимания к оповещениям и уведомлениям.

 Анимация пользовательского интерфейса обычно работает четырьмя способами: Визуализация, привлечение внимания, моделирование и время отклика и индикаторы хода выполнения.

#### <a name="visualize"></a>Визуализация
Анимация может подчеркнуть трехмерную природу объектов и облегчить пользователям визуализацию своей пространственной структуры. Для этого в анимации может потребоваться прокрутка объекта в полном круге, медленное поверх него и немного увеличить его размер, чтобы привлечь внимание к Ролловеру или фокусу.

Хотя трехмерные объекты могут перемещаться с помощью пользовательского элемента управления, конструктор должен заранее определиться (программно или вручную), как лучше анимировать движение, которое обеспечивает оптимальное понимание объекта. Эта программируемая анимация может быть активирована пользователем путем помещения курсора на объект, в то время как перемещаемые пользователем перемещения должны понимать, как манипулировать объектом. Ограничение перемещения до одной оси или ориентации за раз; масштабирование, вращение или перевод, но не более одного одновременно.

Категория визуализации включает в себя аспекты данных, связей, состояния, структуры, последовательности и времени.

##### <a name="data"></a>Данные
Иллюстрация сложной и переменной информации:

- Перемещение по визуализациям информации, таким как диаграммы и графики

- Пошаговая отладка последовательности, интерактивного обзора и разбиения на страницы

- Вызов подробных сведений, указание и выделение конкретной информации

- Перерасположение подробных сведений и дополнительных сведений поверх элемента с упором

- Трансформация из одного структурного или организационного представления в другое

- Представление изменений с течением времени с помощью ползунков времени, регистрацию и выбора и элементов управления транспорта (воспроизведение, остановка и пауза)

##### <a name="relationships"></a>Отношения

- Иллюстрация того, как элементы связаны друг с другом или какие элементы связаны с данным элементом.

- Отображение иерархий и отношений типа "родители-потомки" или одноуровневого отношения

- Один элемент порождает другой

- Один элемент сводится к другому элементу

- Один элемент из одного модема в другой

##### <a name="state"></a>Область

- Обновления содержимого

- Фокус пользователя и выбор

- Ход выполнения

- Ошибки

##### <a name="structure"></a>structure

- Сведение структуры на одном узле

- Переориентация

- Свертывание, развертывание и свертывание

##### <a name="sequence"></a>Последовательность

- Последовательность показа слайдов

- Зеркальное отображение изображений

##### <a name="time"></a>время;

- Показывать изменения со временем, промежуток времени и ролик

- Перейти в корзину, отменить и повторить

- Восстановление исторических состояний

#### <a name="attract-attention"></a>Привлечь внимание
Если цель состоит в том, чтобы привлечь внимание пользователя к одному элементу из нескольких или предупредить пользователя об изменении информации, может оказаться уместной анимация. Например, начальная страница приложения может использовать начало работы кнопку, которую слайды помещают после загрузки страницы.

Как правило, последний элемент перемещения на экране аттрактс внимание пользователя.  В ряде анимированных элементов внимание пользователя будет следовать за последним объектом перемещения.

##### <a name="alert"></a>Предупреждение

- Оповещение пользователя, получение внимания, отображение хода выполнения

- Отображение того, что что-то выполняется правильно или неправильно или отображает изменения хода выполнения или хода выполнения

- Запрашивать у пользователей задачу, например поиск дополнительных сведений в Интернете или изучение текущей задачи

##### <a name="notifications"></a>Уведомления

- Оповещение пользователя о состоянии ошибки

- Прервать работу пользователя, чтобы узнать, хотите ли вы посетить что-нибудь еще

- Аккуратно уведомляет пользователя о том, что процесс завершен или изменен, например, когда загрузка завершена.

#### <a name="simulate"></a>Simulate
В этой категории рассматривается физическое и размерность.

- Иллюстрация того, откуда приходят объекты или куда они переходят

- Развернуть, свернуть или открыть и закрыть

- Сдвиг, прокрутка и поворот страниц

- Стек и z-упорядочение

- Обойма и гармошка

- Зеркальное отображение и поворот пользовательского интерфейса

#### <a name="response-and-progress-indicators"></a>Индикаторы реагирования и хода выполнения
Индикаторы хода выполнения имеют несколько существенных преимуществ:

- Незавершенные и неопределенные индикаторы хода выполнения гарантируют, что пользователь не завершил работу системы и не работает над проблемой.

- Индикаторы депрерывания дают пользователю смысл того, насколько далеко выполняется действие, а также приближение к завершению.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> Шаблоны анимации

### <a name="overview"></a>Обзор
Анимация в Visual Studio предназначена для обслуживания определенной функции без снижения производительности пользователей. Как правило, анимация в Visual Studio должна быть такой:

- Небольшие и ненавязчивые

- Естественное и реалистичное

- Слабая и субдуед

- Быстрый и эффективный

- Неявное, не урезан

На этом рисунке показаны стили анимации, которые мы рекомендуем использовать для Visual Studio. Наиболее часто используется анимация или небольшие анимации вроде исчезновения/исчезновения. Существует ограниченное применение таких анимаций перемещения, как расширение и контракт, изменение позиций X и Y, а затем поворот.

![Рекомендуемые стили анимации для Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202 — a_VSAnimStyles")<br />Рекомендуемые стили анимации для Visual Studio

#### <a name="appear-and-disappear"></a>Появление и исчезновение
В этом шаблоне элемент переключается из видимого в режим ожидания и обратно без анимации перехода.

![Отображение и исчезновение анимации](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202 — b_AppearAndDisappear")<br />Отображение и исчезновение анимации

##### <a name="correct-usage"></a>Правильное использование
Новые элементы пользовательского интерфейса, которые должны мгновенно появляться или исчезать, чтобы пользователь не был ни отвлекается, ни неограниченным. Кроме того, анимация с медленным перемещением может восприниматься как перетаскивание, что не происходит при использовании стиля «появление и исчезновение».

##### <a name="incorrect-usage"></a>Неправильное использование
Случаи, когда пользовательский интерфейс выглядит настолько внезапно, что произошло, и Добавление анимации может помочь в контекстном понимании.

##### <a name="animation-properties"></a>Свойства анимации
Задержка времени обычно равна нулю секундам.

##### <a name="examples"></a>Примеры
- Автоматическое скрытие окон инструментов

- Пользовательский интерфейс редактора с активированной клавиатурой, например IntelliSense и Справка по параметрам

- Разворачивание и свертывание областей кода

#### <a name="fade-in-and-fade-out"></a>Появление и исчезание
При использовании этого шаблона элемент пользовательского интерфейса переходит от невидимого (0% Opacity) к видимому (непрозрачность 100%) или наоборот.

![Анимация затухания и затухания](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202 — c_FadeInFadeOut")<br />Анимация затухания и затухания

##### <a name="correct-usage"></a>Правильное использование
Это наиболее часто Рекомендуемая Анимация пользовательского интерфейса. Это незаметное воздействие, которое добавляет интерес без прерывания потока. В некоторых случаях пользователь может даже не понимать, что есть анимация, перцеивинг гладкую и потоковую систему пользовательского интерфейса.

##### <a name="animation-properties"></a>Свойства анимации

- Запуск непрозрачности: 0% для постепенного исчезновения, 100% для затухания

- Завершение непрозрачности: 100% для постепенного исчезновения, 0% для затухания

- Длительность: 200 мс изолированная, 100 мс при использовании в сочетании последовательности анимации

- Стиль замедления: синус InOut

##### <a name="examples"></a>Примеры

- Автоматическое скрытие окон инструментов

- Откройте и закройте меню

- Переходы на фоновый и передний вкладка

#### <a name="color-blend-from-a-to-b"></a>Смешение цветов от A к B
При использовании этого шаблона элемент пользовательского интерфейса меняется с Color на цвет B.

![Анимация смешения цветов](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202 — d_ColorBlend")<br />Анимация смешения цветов

##### <a name="correct-usage"></a>Правильное использование
Как анимированный переход, когда элемент пользовательского интерфейса изменяет цвет из одного контекста или состояния на другое.

##### <a name="animation-properties"></a>Свойства анимации

- Начальный цвет: зависит от пользовательского интерфейса

- Конечный цвет: особый для пользовательского интерфейса

- Длительность: 200 мс изолированная, 100 мс при использовании в сочетании последовательности анимации

- Стиль замедления: синус InOut

##### <a name="examples"></a>Примеры

- Переходы состояния окна документа (активные, последние активные и неактивные)

- Переходы состояния окна инструментов (с фокусом и без фокуса)

#### <a name="expand-and-contract"></a>Развернуть и свернуть
При использовании этого шаблона элемент пользовательского интерфейса расширяется по осям X, Y или обоим направлениям.

![Развернуть и свернуть анимацию](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202 — e_ExpandContract")<br />Развернуть и свернуть анимацию

##### <a name="correct-usage"></a>Правильное использование
Как анимированный переход при изменении размера элемента пользовательского интерфейса с одного контекста на другой.

##### <a name="animation-properties"></a>Свойства анимации

- Масштаб X:% или определенное измерение (в пикселях)

- Масштаб Y:% или определенное измерение (в пикселях)

- Расположение привязки: обычно верхний левый угол (для языков слева направо) или верхний правый (для языков с письмом справа налево).

- Длительность: 200 мс изолированная, 100 мс при использовании в сочетании последовательности анимации

##### <a name="examples"></a>Примеры

- Панель обозревателя архитектуры — развернуть и свернуть

- Развертывание и свертывание элемента начальной страницы Visual Studio 2017

#### <a name="x-y-position-change"></a>Изменение расположения X-Y
При использовании этого шаблона элемент пользовательского интерфейса изменяет свое расположение X или Y или оба значения.

![Анимация изменения расположения X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202 — f_XYPositionChange")<br />Анимация изменения расположения X-Y

##### <a name="correct-usage"></a>Правильное использование
Как анимированный переход, когда элемент пользовательского интерфейса меняет расположение с одного контекста на другой.

##### <a name="animation-properties"></a>Свойства анимации

- Начальное расположение X и Y: для конкретного пользовательского интерфейса

- Конечная позиция X и Y: зависит от пользовательского интерфейса

- Путь перемещения: нет

- Длительность: 200 мс изолированная, 100 мс при использовании в сочетании последовательности анимации

- Стиль замедления: синус InOut

##### <a name="example"></a>Пример
Изменение порядка вкладок

#### <a name="rotate"></a>Rotate
При использовании этого шаблона элемент пользовательского интерфейса поворачивается.

![Анимация поворота элемента пользовательского интерфейса](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202 — g_Rotate")<br />Анимация поворота элемента пользовательского интерфейса

##### <a name="correct-usage"></a>Правильное использование
Только для неопределенного индикатора хода выполнения.

##### <a name="animation-properties"></a>Свойства анимации

- Степень поворота: 360

- Центр вращения: середина объекта

- Длительность: непрерывная

##### <a name="example"></a>Пример
Неопределенный индикатор хода выполнения (цикличный)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Общие действия с ИНТЕРФЕЙСом оболочки и Рекомендуемые анимации

#### <a name="tab-open"></a>Вкладка "Открыть"
![Анимация открытия вкладки](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202 — h_TabOpen")<br />Анимация открытия вкладки

- Стиль: отображается

- Длительность: ноль секунд

#### <a name="tab-close"></a>Закрыть вкладку
![Анимация закрытия вкладки](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202 — i_TabClose")<br />Анимация закрытия вкладки

- Стиль: изменение расположения по оси X

- Длительность: 200 мс

#### <a name="tab-reorder"></a>Изменение порядка вкладок
![Анимация переупорядочивания вкладок в Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202 — j_TabReorder")<br />Анимация изменения порядка вкладок

- Стиль: изменение расположения по оси X

- Длительность: 200 мс

#### <a name="close-floating-document"></a>Закрыть плавающий документ
![Закрыть анимацию с плавающей документом](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202 — k_CloseFloatingDocument")<br />Закрыть анимацию с плавающей документом

- Стиль: отображается

- Длительность: 200 мс

#### <a name="window-state-transition"></a>Переход к состоянию окна
![Анимация перехода состояния окна](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202 — l_WindowStateTransition")<br />Анимация перехода состояния окна

- Стиль: чтобы соответствовать другим окнам, позвольте текущей операционной системе определить анимацию закрытия документа.

- Длительность: 200 мс

#### <a name="menu-open"></a>Открыть меню
![Открыть анимацию меню](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202 — m_MenuOpen")<br />Открыть анимацию меню

- Стиль: выцветание

- Длительность: 200 мс

#### <a name="menu-close"></a>Закрыть меню
![Закрыть анимацию меню](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202 — n_MenuClose")<br />Закрыть анимацию меню

- Стиль: затухание

- Длительность: 200 мс

#### <a name="auto-hide-tool-window-reveal"></a>Автоматическое скрытие отображения окна инструментов
![Отображать анимацию при автоскрытии окна инструментов](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202 — o_AutoHideToolWindowReveal")<br />Отображать анимацию при автоскрытии окна инструментов

- Стиль: отображается

- Длительность: ноль секунд
