---
title: Выполнение сборки для Azure с помощью командной строки | Документация Майкрософт
description: Создание сборки для Azure с помощью командной строки
services: visual-studio-online
author: ghogen
manager: douge
assetId: 94b35d0d-0d35-48b6-b48b-3641377867fd
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
origin.date: 03/05/2017
ms.date: 09/10/2018
ms.author: v-junlch
ms.openlocfilehash: bc65d64f4dad2ac38c1f0c64ce6c7297d3c37d3a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62572426"
---
# <a name="building-azure-projects-from-the-command-line"></a>Создание проектов Azure с помощью командной строки
С помощью Microsoft Build Engine (MSBuild) можно выполнять сборку продуктов в лабораторных средах, где приложение Visual Studio не установлено. MSBuild использует для файлов проекта расширяемый формат XML, который полностью поддерживается Майкрософт. С помощью формата файлов MSBuild вы можете описать, какие именно элементы должны быть собраны для одной или нескольких платформ и конфигураций.

MSBuild можно также запускать из командной строки. В этой статье описывается именно такой метод. Задавая свойства в командной строке, вы можете собирать те или иные конфигурации проекта. Точно так же вы можете определять объекты, которые создает MSBuild. Дополнительные сведения о параметрах командной строки и MSBuild см. в [справочнике по командной строке MSBuild](https://msdn.microsoft.com/library/ms164311.aspx).

## <a name="msbuild-parameters"></a>Параметры MSBuild
Самый простой способ создать пакет — запустить MSBuild с параметром `/t:Publish` . По умолчанию эта команда создает каталог в зависимости от корневой папки для проекта, например `<ProjectDirectory>\bin\Configuration\app.publish\`. При сборке проекта Azure создается два файла — собственно файл пакета и сопутствующий файл конфигурации:

- файл пакета (`project.cspkg`);
- файл конфигурации (`ServiceConfiguration.TargetProfile.cscfg`).

По умолчанию каждый проект Azure включает в себя один файл конфигурации службы для локальных сборок (отладка) и один — для облачных (промежуточное хранение или производство). Но файлы конфигурации службы можно добавлять или удалять по необходимости. При сборке пакета в Visual Studio вам предлагается выбрать файл конфигурации службы для включения в пакет. При сборке пакета с помощью MSBuild файл конфигурации локальной службы добавляется по умолчанию. Чтобы добавить другой файл конфигурации, задайте свойство `TargetProfile` команды MSBuild (`MSBuild /t:Publish /p:TargetProfile=ProfileName`).

Если вы хотите использовать другой каталог для хранения пакета и файлов конфигурации, задайте путь с помощью параметра `/p:PublishDir=Directory\` (включая разделитель в виде обратной косой черты в конце).

## <a name="next-steps"></a>Следующие шаги
Когда пакет скомпилирован, его можно развернуть в Azure.

<!-- Update_Description: update metedata properties -->