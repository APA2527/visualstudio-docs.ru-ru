---
title: Publish-WebApplicationVM | Документация Майкрософт
description: Узнайте, как развернуть веб-приложение на виртуальной машине. Этот сценарий создает необходимые ресурсы в подписке Azure, если они еще не созданы.
author: ghogen
manager: jillfra
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: e35f5decee2a908a9d1075ff3f6365a1d358c7b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "70739311"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (сценарий Windows PowerShell)
Развертывание веб-приложения на виртуальной машине. и создает необходимые ресурсы в подписке Azure, если они еще не созданы.

```
Publish-WebApplicationVM
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-VMPassword @{Name = "name"; Password = "password")
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

### <a name="configuration"></a>Конфигурация
Путь к файлу конфигурации JSON, содержащему подробные сведения о развертывании.

| Aliases | нет |
| --- | --- |
| Необходим? |Да |
| Положение |именованный |
| Значение по умолчанию |нет |
| Принимать входные данные конвейера? |false |
| Принимать символы-шаблоны? |false |

### <a name="subscriptionname"></a>Параметр SubscriptionName
Имя подписки Azure, в которой необходимо создать виртуальную машину.

| Aliases | нет |
| --- | --- |
| Необходим? |false |
| Положение |именованный |
| Значение по умолчанию |Используется первая подписка в файле подписок |
| Принимать входные данные конвейера? |false |
| Принимать символы-шаблоны? |false |

### <a name="webdeploypackage"></a>Параметр WebDeployPackage
Путь к пакету веб-развертывания для публикации на виртуальной машине. Этот пакет можно создать с помощью мастера «Публикация веб-сайта» в Visual Studio. Ознакомьтесь со статьей [Как создать пакет веб-развертывания в Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx).

| Aliases | нет |
| --- | --- |
| Необходим? |false |
| Положение |именованный |
| Значение по умолчанию |нет |
| Принимать входные данные конвейера? |false |
| Принимать символы-шаблоны? |false |

### <a name="allowuntrusted"></a>AllowUntrusted
Значение true позволяет использовать сертификаты, не подписанные надежным корневым центром сертификации.

| Aliases | нет |
| --- | --- |
| Необходим? |false |
| Положение |именованный |
| Значение по умолчанию |false |
| Принимать входные данные конвейера? |false |
| Принимать символы-шаблоны? |false |

### <a name="vmpassword"></a>VMPassword
Данные учетной записи виртуальной машины. Пример: -VMPassword @{Name = admin; Password = password}

| Aliases | нет |
| --- | --- |
| Необходим? |false |
| Положение |именованный |
| Значение по умолчанию |нет |
| Принимать входные данные конвейера? |false |
| Принимать символы-шаблоны? |false |

### <a name="databaseserverpassword"></a>Параметр DatabaseServerPassword
Учетные данные для базы данных SQL в Azure. Пример: -DatabaseServerPassword @{Name = admin; Password = password}

| Aliases | нет |
| --- | --- |
| Необходим? |false |
| Положение |именованный |
| Значение по умолчанию |нет |
| Принимать входные данные конвейера? |false |
| Принимать символы-шаблоны? |false |

### <a name="sendhostmessagestooutput"></a>Параметр SendHostMessagesToOutput
Если установлено значение true, оправляет сообщения из сценария в поток вывода.

| Aliases | нет |
| --- | --- |
| Необходим? |false |
| Положение |именованный |
| Значение по умолчанию |false |
| Принимать входные данные конвейера? |false |
| Принимать символы-шаблоны? |false |

## <a name="remarks"></a>Remarks
Подробное описание того, как использовать сценарий для создания сред разработки и тестирования, см. в статье [Использование скриптов Windows PowerShell для публикации в среды разработки и тестирования](vs-azure-tools-publishing-using-powershell-scripts.md).

В файле конфигурации JSON указаны данные объектов, которые необходимо развернуть. Он содержит сведения, указанные при создании проекта, например имя, группу сходства, образ виртуального жесткого диска и размер виртуальной машины. Он также включает конечные точки виртуальной машины, подготавливаемые базы данных (если они есть) и параметры веб-развертывания. В следующем коде показан пример файла конфигурации JSON.

```
{
    "environmentSettings": {
        "cloudService": {
            "name": "myvmname",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myvmname",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Windows-Server-2012-R2-201404.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [
                    {
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [
            {
                "connectionStringName": "",
                "databaseName": "",
                "serverName": "",
                "user": "",
                "password": ""
            }
        ],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

В файле конфигурации JSON можно изменить объекты, которые подлежат подготовке. Виртуальная машина и облачная служба необходимы, но раздел баз данных является необязательным.
