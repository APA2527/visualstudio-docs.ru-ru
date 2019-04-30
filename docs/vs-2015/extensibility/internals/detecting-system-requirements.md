---
title: Определение требований к системе | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 51
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 467554b8e50878bcdf1029e4792bbf168a09fa11
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445247"
---
# <a name="detecting-system-requirements"></a>Определение требований к системе
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пакет VSPackage не может работать, если не установлена среда Visual Studio. При использовании установщика Windows для управления установкой вашего VSPackage, можно настроить программу установки, чтобы обнаруживать наличие установленного Visual Studio. Кроме того, можно также настроить для проверки системы другие требования, например, на конкретную версию Windows или определенный объем ОЗУ.  
  
## <a name="detecting-visual-studio-editions"></a>Обнаружение выпуски Visual Studio  
 Чтобы определить, установлен ли выпуск Visual Studio, убедитесь, что значение раздела реестра Install (REG_DWORD) 1 в соответствующую папку, как показано в следующей таблице. Обратите внимание, что иерархия выпуски Visual Studio:  
  
1. Предприятие  
  
2. Professional  
  
3. Сообщество  
  
   При установке «выше» edition добавляются разделы реестра для этого выпуска также, как и для выпусков «ниже». То есть если установлен выпуск Enterprise, ключ установки равен 1, для предприятия, а также в выпусках Professional и Community. Поэтому необходимо проверить только «высокий» выпуск, что нужно.  
  
> [!NOTE]
> 32-разрядные ключи в 64-разрядной версии редактора реестра, указанных в списке HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\. Visual Studio приведены в разделе HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\.  
  
|Продукт|Ключ|  
|-------------|---------|  
|Visual Studio Enterprise|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Оболочка Visual Studio 2015 (интегрированная и изолированная)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Обнаружение при запуске Visual Studio  
 Не удается зарегистрировать VSPackage правильно, если Visual Studio выполняется в том случае, когда объект VSPackage установлен. Установщик должен определять, когда выполняется Visual Studio и отклонять для установки программы. Установщик Windows не позволяет использовать записи таблицы для включения такого обнаружения. Вместо этого необходимо создать настраиваемое действие, следующим образом: Используйте `EnumProcesses` функция для обнаружения процесса devenv.exe и затем либо задать свойство установщика, используемый в условие запуска или по условию отображать диалоговое окно, которое предлагает пользователю закрыть Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
