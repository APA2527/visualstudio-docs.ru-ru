---
title: Импорт и экспорт параметров — команда | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 91b34183e36c86290c14e3da7d17687d45cfe180
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694661"
---
# <a name="import-and-export-settings-command"></a>Импорт и экспорт параметров - команда
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Импортирует, экспортирует или сбрасывает параметры [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>Переключатели  
 /export:`filename`  
 Необязательный параметр. Экспортирует текущие параметры в указанный файл  
  
 /import:`filename`  
 Необязательный параметр. Импортирует текущие параметры в указанный файл  
  
 /reset  
 Необязательный параметр. Сбрасывает текущие параметры  
  
## <a name="remarks"></a>Примечания  
 Выполнение этой команды без параметров командной строки открывает мастер **Импорт и экспорт параметров**. Дополнительные сведения см. в статье [Практическое руководство. Совместное использование параметров на разных компьютерах или в разных версиях Visual Studio](https://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## <a name="example"></a>Пример  
 Следующая команда экспортирует текущие параметры в файл `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
