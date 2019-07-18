---
title: Практическое руководство. Настройка безопасности списка включения
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ef4d25088e56f2223cb392dbc00c8454e1a291ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62826383"
---
# <a name="how-to-configure-inclusion-list-security"></a>Практическое руководство. Настройка безопасности списка включения
  Если у вас есть разрешения администратора, вы можете настроить [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] запросы о доверии к элементу управления ли конечные пользователи получают возможность установки решений Office, сохранив решение о доверии в списке включения. Сведения о списках включений, см. в разделе [доверия Office решения с помощью списков включения](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Для решений, находящихся в каждой из пяти зон можно задать следующие параметры:

- Включить [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] раздела запроса о доверии и в список включения. Можно разрешить конечным пользователям предоставлять доверие решениям Office, подписанные с использованием любого сертификата.

- Ограничить [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] раздела запроса о доверии и в список включения. Можно разрешить конечным пользователям для установки решений Office, подписанным сертификатом, который идентифицирует издателя, но который еще не является доверенным.

- Отключить [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] раздела запроса о доверии и в список включения. Можно запретить пользователям установку любого решения Office, которая не подписана с явно доверенным сертификатом.

## <a name="enable-the-inclusion-list"></a>Включение списка
 Включите список включения для зоны, если нужно, чтобы конечные пользователи могут быть представлены с параметром установки и запуска любого решения Office, которые поступают из этой зоны.

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Чтобы включить в список включения с помощью редактора реестра

1. Откройте редактор реестра:

    1. Щелкните **Пуск**, а затем **Выполнить**.

    2. В **откройте** введите **regedt32.exe**, а затем нажмите кнопку **ОК**.

2. Найдите следующий раздел реестра:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Если ключ не существует, создайте его.

3. Добавьте следующие подразделы как **строковое значение**, если они еще не существуют, со связанными значениями.

    |Строковое значение подраздела|Значение|
    |-------------------------|-----------|
    |**Интернет**|**AuthenticodeRequired**|
    |**UntrustedSites**|**Отключено**|
    |**Мой компьютер**|**Включено**|
    |**Локальная интрасеть**|**Включено**|
    |**TrustedSites**|**Включено**|

     По умолчанию **Internet** имеет значение **AuthenticodeRequired** и **UntrustedSites** имеет значение **отключено**.

### <a name="to-enable-the-inclusion-list-programmatically"></a>Программное Включение в список включения

1. Создайте консольное приложение Visual Basic или Visual C#.

2. Откройте *Program.vb* или *Program.cs* файл для редактирования и добавьте следующий код.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "AuthenticodeRequired")
    key.SetValue("TrustedSites", "Enabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Enabled");
    key.SetValue("LocalIntranet", "Enabled");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "Enabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Выполните сборку и запуск приложения.

## <a name="restrict-the-inclusion-list"></a>Ограничение списка включения
 Ограничение списка включения, чтобы решения, которые должны быть подписаны с сертификатом Authenticode, идентифицирующим пользователям предлагается решение о доверии.

### <a name="to-restrict-the-inclusion-list"></a>Для ограничения списка включения

1. Откройте редактор реестра:

    1. Щелкните **Пуск**, а затем **Выполнить**.

    2. В **откройте** введите **regedt32.exe**, а затем нажмите кнопку **ОК**.

2. Найдите следующий раздел реестра:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Если ключ не существует, создайте его.

3. Добавьте следующие подразделы как **строковое значение**, если они еще не существуют, со связанными значениями.

    |Строковое значение подраздела|Значение|
    |-------------------------|-----------|
    |**UntrustedSites**|**Отключено**|
    |**Интернет**|**AuthenticodeRequired**|
    |**Мой компьютер**|**AuthenticodeRequired**|
    |**Локальная интрасеть**|**AuthenticodeRequired**|
    |**TrustedSites**|**AuthenticodeRequired**|

     По умолчанию **Internet** имеет значение **AuthenticodeRequired** и **UntrustedSites** имеет значение **отключено**.

### <a name="to-restrict-the-inclusion-list-programmatically"></a>Ограничение списка включения программными средствами

1. Создайте консольное приложение Visual Basic или Visual C#.

2. Откройте *Program.vb* или *Program.cs* файл для редактирования и добавьте следующий код.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "AuthenticodeRequired")
    key.SetValue("LocalIntranet", "AuthenticodeRequired")
    key.SetValue("Internet", "AuthenticodeRequired")
    key.SetValue("TrustedSites", "AuthenticodeRequired")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "AuthenticodeRequired");
    key.SetValue("LocalIntranet", "AuthenticodeRequired");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "AuthenticodeRequired");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Выполните сборку и запуск приложения.

## <a name="disable-the-inclusion-list"></a>Отключение списка включения
 Таким образом, чтобы конечные пользователи могут только устанавливать решения, которые подписаны сертификатом, надежным и известным можно отключить в список включения.

### <a name="to-disable-the-inclusion-list"></a>Отключение списка включения

1. Откройте редактор реестра:

    1. Щелкните **Пуск**, а затем **Выполнить**.

    2. В **откройте** введите **regedt32.exe**, а затем нажмите кнопку **ОК**.

2. Если это еще не существует, создайте следующий раздел реестра:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

3. Добавьте следующие подразделы как **строковое значение**, если они еще не существуют, со связанными значениями.

    |Строковое значение подраздела|Значение|
    |-------------------------|-----------|
    |**UntrustedSites**|**Отключено**|
    |**Интернет**|**Отключено**|
    |**Мой компьютер**|**Отключено**|
    |**Локальная интрасеть**|**Отключено**|
    |**TrustedSites**|**Отключено**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>Чтобы отключить список включения программными средствами

1. Создайте консольное приложение Visual Basic или Visual C#.

2. Откройте *Program.vb* или *Program.cs* файл для редактирования и добавьте следующий код.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Disabled")
    key.SetValue("LocalIntranet", "Disabled")
    key.SetValue("Internet", "Disabled")
    key.SetValue("TrustedSites", "Disabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Disabled");
    key.SetValue("LocalIntranet", "Disabled");
    key.SetValue("Internet", "Disabled");
    key.SetValue("TrustedSites", "Disabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();

    ```

3. Выполните сборку и запуск приложения.

## <a name="see-also"></a>См. также
- [Доверия решениям Office с помощью списков включения](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Безопасные решения Office](../vsto/securing-office-solutions.md)
