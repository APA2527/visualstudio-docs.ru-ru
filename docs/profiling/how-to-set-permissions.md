---
title: Установка разрешений | Документация Майкрософт
description: В этой статье описывается процедура предоставления администратором компьютера разрешений безопасности, необходимых для профилирования, пользователю или группе, не имеющим прав администратора.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 550c8c3f7a436fa2321d42ced1744650d4de679f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906984"
---
# <a name="how-to-set-permissions"></a>Практическое руководство. Настройка разрешений

В этом разделе описано, как администратор компьютера может предоставить разрешения безопасности, необходимые для профилирования, пользователю или группе без прав администратора на этом компьютере.

Основной принцип безопасности заключается в том, что приложения должны выполняться с уровнем разрешений, не превышающим необходимый. Этот принцип также применим и к пользователям. Если пользователи могут эффективно выполнять свою работу, входя в систему как члены группы "Пользователи", а не "Администраторы", им не следует предоставлять разрешения администратора. В первой процедуре "Создание учетной записи пользователя с разрешениями пользователя" описывается создание учетной записи пользователя для члена группы "Пользователи".

Членам группы "Пользователи" потребуется доступ к папкам и файлам на диске, используемым совместно с другими членами команды. Во второй процедуре "Предоставление доступа к общим файлам проекта" описывается порядок предоставления доступа.

Члены группы "Пользователи" могут запускать средства профилирования, если администратор предоставил им доступ к программному драйверу для этих средств. В последней процедуре, "Предоставление доступа к драйверу профилирования" описано, как предоставить доступ к этому драйверу.

> [!NOTE]
> Для выполнения действий в этих процедурах требуются права администратора.

## <a name="to-create-a-user-account-that-has-user-permissions"></a>Создание учетной записи пользователя с разрешениями пользователя

1. Щелкните правой кнопкой мыши **Мой компьютер** и выберите пункт **Управление**.

     Откроется окно **Управление компьютером**.

2. Разверните узел **Локальные пользователи и группы**.

3. Правой кнопкой мыши щелкните папку **Пользователи** и выберите команду **Создать пользователя**.

     Появится диалоговое окно **Создание пользователя**.

4. Заполните поля в этом окне, указав сведения о создаваемой учетной записи пользователя. Укажите пароль. При необходимости установите флажок с требованием сменить пароль при следующем входе в систему.

5. Нажмите кнопку **Создать**, а затем кнопку **Закрыть**.

     Новый пользователь отображается в группе "Пользователи", группе пользователей, не обладающих правами администратора.

## <a name="to-grant-access-to-shared-project-files"></a>Предоставление доступа к общим файлам проекта

1. В проводнике Windows перейдите в корневой каталог дерева папок для файлов проекта, используемых этим пользователем и общих для командного проекта.

     Путь к этой папке может выглядеть следующим образом:

    ```cmd
    D:\ourProject
    ```

2. Щелкните папку правой кнопкой мыши и выберите пункт **Свойства**.

     Откроется диалоговое окно **\<folder name>Свойства**.

3. Перейдите на вкладку **Безопасность** .

4. Щелкните имя учетной записи пользователя в поле **Группы или пользователи**.

5. В поле **Разрешения для \<user name>** установите флажок **Полный доступ**.

6. Нажмите кнопку **ОК**.

     При этом пользователю будут предоставлены разрешения для доступа к дереву общих папок, которое начинается с папки, выбранной на шаге 5.

## <a name="to-grant-access-to-the-profiling-driver"></a>Предоставление доступа к драйверу профилирования

1. Откройте командную строку от имени учетной записи администратора.

2. Измените каталог на:

    ```cmd
    <drive>:\Program Files\Microsoft Visual Studio 14\Team Tools\Performance Tools
    ```

3. Выполните следующую команду:

    ```cmd
    vsperfcmd /admin:driver,start /admin:service,start
    ```

     Эта команда устанавливает и запускает драйвер для средств профилирования.

     Эта команда запускает драйвер и службу профилирования, чтобы пользователи без прав администратора могли использовать функции профилирования, доступные в пространстве их пользовательских процессов. Только администратор может выполнить команду; она завершается ошибкой для обычных пользователей.

     Обратите внимание, что результат выполнения данного шага отменяется после перезагрузки компьютера, если не выполнить последний шаг в этой процедуре.

4. Выполните эту команду, чтобы разрешить доступ к функциям драйвера для пользователя или группы, не имеющих административных прав на компьютере:

    ```cmd
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>
    ```

     При этом учетной записи \<user name> или \<group name> предоставляется доступ к средствам профилирования. Параметр \<right> определяет функции профилирования, к которым предоставляется доступ. Параметр \<right> может иметь одно или несколько из следующих значений:

    - FullAccess — предоставляет доступ ко всем методам профилирования, включая сбор данных о производительности из служб, выборки и профилирования в нескольких сеансах.

    - SampleProfiling — предоставляет доступ к методам профилирования с выборкой.

    - CrossSession — предоставляет доступ к профилированию в нескольких сеансах, необходимый для служб профилирования.

5. (Необязательно) Чтобы сохранить результаты любого из предыдущих шагов после перезагрузки компьютера, выполните следующую команду:

    ```cmd
    vsperfcmd /admin:driver,autostart,on
    ```

   Указанные пользователи после входа в систему будут иметь возможность использовать средства профилирования без прав администратора.

## <a name="see-also"></a>См. также

[Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)
[VSPerfCmd](../profiling/vsperfcmd.md)
[Профилирование и безопасность Windows Vista](../profiling/profiling-and-windows-vista-security.md)
