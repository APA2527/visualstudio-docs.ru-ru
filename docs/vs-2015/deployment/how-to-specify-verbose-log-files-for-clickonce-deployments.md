---
title: Как указать подробные файлы журнала для развертываний ClickOnce | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 78fa278952004348e035a675a1e159b2164285b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843244"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Практическое руководство. Указание подробных файлов журнала для развертывания ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] поддерживает файлы журналов действий для всех развертываний. В этих журналах содержатся сведения, относящиеся к установке, инициализации, обновлению и удалению [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания. Чтобы увеличить детализацию [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] записи в эти файлы журнала, используйте редактор реестра (**regedit.exe**), чтобы указать уровень детализации.  
  
> [!CAUTION]
> Неправильное использование редактора реестра может привести к серьезным проблемам, которые могут потребовать переустановки операционной системы. Используйте редактор реестра на свой страх и риск.  
  
 Следующая процедура описывает, как указать уровень детализации для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] файлов журнала для текущего пользователя. Чтобы уменьшить уровень детализации, удалите это значение реестра.  
  
### <a name="to-specify-verbose-log-files"></a>Указание подробных файлов журнала  
  
1. Откройте **Regedit.exe**.  
  
2. Перейдите к узлу `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .  
  
3. При необходимости создайте новое строковое значение с именем `LogVerbosityLevel` .  
  
4. Установите для `LogVerbosityLevel` значение `1`.  
  
## <a name="see-also"></a>См. также:  
 [Устранение неполадок развертывания ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
