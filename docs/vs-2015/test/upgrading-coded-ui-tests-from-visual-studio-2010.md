---
title: Upgrading Coded UI Tests
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 35
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3a29e531ca9b2a74e67abf80a0e3017a0f5b0b07
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298004"
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Обновление закодированных тестов пользовательского интерфейса с версии Visual Studio 2010
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Тестовые проекты, содержащие закодированные тесты пользовательского интерфейса, которые созданы в [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1, автоматически восстанавливаются при открытии их в Visual Studio 2012. Если тестовые проекты помещаются в систему управления версиями, файлы проектов извлекаются для этого восстановления. После восстановления эти тестовые проекты, содержащие закодированные тесты пользовательского интерфейса, можно использовать в [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 и [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

 **Requirements**

- Visual Studio Enterprise

> [!NOTE]
> Visual Studio включает несколько типов тестового проекта. Если вы создадите новый закодированный тест пользовательского интерфейса, он будет создан в типе проекта закодированных тестов пользовательского интерфейса. Дополнительные сведения см. в разделе [Обновление тестов из более ранних версий Visual Studio](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).

> [!WARNING]
> Тестовые проекты[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] , содержащие закодированные тесты пользовательского интерфейса, необходимо перестроить при открытии тестового проекта в [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] или [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] параллельно с [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!WARNING]
> Когда тестовый проект, созданный в [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] и содержащий только модульные тесты, открывается в [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], закодированные тесты пользовательского интерфейса невозможно добавить к нему. Также не получится добавить закодированный тест пользовательского интерфейса в проект модульных тестов, созданный в [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Проблемы совместимости между Visual Studio 2010 и Visual Studio 2012
 Следующая таблица перечисляет проблемы закодированных тестов пользовательского интерфейса между [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] и [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!CAUTION]
> Известна проблема с ссылками в проектах закодированных тестов пользовательского интерфейса, которые не появляются в обозревателе решений. Дополнительные сведения см. в файле сведений, который включен в установочный носитель [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .

|Функции закодированного пользовательского интерфейса|Проблемы|Решение|
|----------------------------|-----------|--------------|
|Тестирование пользовательского интерфейса Silverlight в [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]не поддерживается|**Сборка завершится ошибкой**<br /><br /> Если у вас имеется пакет 2 дополнительных компонентов [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] и вы создали проекты закодированных тестов пользовательского интерфейса для приложений Silverlight, то эти проекты не получится открыть в [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Рекомендуется управлять этими проектами только в пакете дополнительных компонентов [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2.|
|Тестирование пользовательского интерфейса Firefox в [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]не поддерживается|**Сборка будет выполнена успешно, тестовый запуск завершится ошибкой**<br /><br /> Если у вас имеется пакет 2 дополнительных компонентов [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] и вы создали проекты закодированных тестов пользовательского интерфейса для веб-приложений в Firefox, то эти проекты не получится открыть в [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Рекомендуется управлять этими проектами только в пакете дополнительных компонентов [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2.|
|Новые интерфейсы API тестирования кода пользовательского интерфейса были добавлены в [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Сборка завершится ошибкой**<br /><br /> Если вы создали закодированные тесты пользовательского интерфейса с помощью нового API тестирования пользовательского интерфейса в [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], эти проекты не получится открыть в [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].|Проекты с новым API должны управляться только в [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .|
|В [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]ссылки были добавлены в оператор "Choose" в CSPROJ-файле. В [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]мы используем файл целевых объектов обратной связи для включения ссылок на сборки закодированных тестов пользовательского интерфейса.|В [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], закодированный тест пользовательского интерфейса не получится добавить в тестовый проект, созданный в [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] (или SP1), который не содержит закодированный тест пользовательского интерфейса.<br /><br /> Процесс восстановления добавляет целевые файлы и оператор выбора. Если закодированного теста пользовательского интерфейса нет в тестовом проекте, проект помечается как восстановленный, и соответствующие ссылки не будут добавлены во время добавления закодированного теста пользовательского интерфейса в [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Вам необходимо создать новый тестовый проект в том же решении с помощью [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] и добавить в него новый закодированный тест пользовательского интерфейса. Кроме того, вы можете добавить закодированные тесты пользовательского интерфейса в тестовый проект в [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 и открыть этот проект в [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|

## <a name="UpgradingCodedUIFromVS2010_Update"></a> Обновление Visual Studio 2010 с пакетом обновления 1 (SP1)
 Обновление до [!INCLUDE[vs2010](../includes/vs2010-md.md)] с пакетом обновления 1 (SP1) с поддержкой совместимости для Visual Studio 2012 и Windows 8 доступно для загрузки в [Центре загрузки Microsoft](https://www.microsoft.com/download/details.aspx?id=34677) , а также как обновление Visual Studio.

 После применения обновления улучшатся следующие функции средства закодированного теста пользовательского интерфейса [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 для Windows 8.

- Можно запустить закодированный тест пользовательского интерфейса для элементов управления Windows Presentation Foundation (WPF) на основе платформы Microsoft .NET Framework 4.5 на компьютере, на котором запущена Windows 8.

- Можно выполнить закодированный тест пользовательского интерфейса для 64-разрядного (x64) Internet Explorer 10 на компьютере, на котором запущена Windows 8.

  Обновление также содержит исправления для следующих проблем:

- **Покрытия кода:** неспособность открыть файл покрытия кода (.coverage), созданный Visual Studio 2012 в [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1.

- **Затруднительные артефакты теста:** в вашей команде есть артефакт теста, присвоенный недопустимому пользователю в Team Foundation Server (TFS) 2010. Например, пользователь покинул компанию, но по-прежнему обладает тестовым случаем, присвоенным ему. Обновление Team Foundation Server 2010 до Team Foundation Server 2012. Вы используете [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010 для подключения к обновленным серверам Team Foundation Server. Вам не удается присвоить артефакт теста какому-либо пользователю Team Foundation Server с помощью [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010.

- **Нагрузочное тестирование:** при выполнении нагрузочного теста вместе с типом сети, отличным от профиля локальной сети (LAN) на компьютере с Windows 8, драйвер эмулятора сети вызывает сбой операционной системы. Дополнительные сведения см. в [статье базы знаний 2736182](https://support.microsoft.com/help/2736182/a-gdr-update-for-visual-studio-2010-sp1-is-available-to-add-compatibil).

## <a name="see-also"></a>См. также раздел
 [Porting, Migrating, and Upgrading Visual Studio Projects](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [Upgrading Tests from Earlier Versions of Visual Studio](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52) [Use UI Automation To Test Your Code](../test/use-ui-automation-to-test-your-code.md) [Generating a Coded UI Test from an Existing Action Recording](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [Supported Configurations and Platforms for Coded UI Tests and Action Recordings](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
