---
title: -Out (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e1f20b446d355ea0cbc6700de5f2e6f79de51d09
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59647065"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Задает файл для хранения и отображения ошибок при запуске, создании, перестроении или развертывании решения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv /out FileName  
```  
  
## <a name="arguments"></a>Аргументы  
 `FileName`  
 Обязательный. Путь и имя файла для приема ошибок при сборке исполняемого файла.  
  
## <a name="remarks"></a>Примечания  
 Если указано несуществующее имя файла, такой файл создается автоматически. Если файл уже существует, то результаты добавляются к имеющемуся в нем содержимому.  
  
 Ошибки сборки в командной строке отображаются в окне **Команда** и представлении "Построитель решений" окна **Вывод**. Этот параметр полезен, если вы выполняете автоматические сборки и хотите видеть результаты.  
  
## <a name="example"></a>Пример  
 Этот пример запускает `MySolution` и записывает ошибки в файл `MyErrorLog.txt`.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
