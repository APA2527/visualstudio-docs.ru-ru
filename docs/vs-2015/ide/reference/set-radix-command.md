---
title: Команда "Задать основание системы счисления" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bee6368931dc47b78186ec870039ab292960fa77
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654078"
---
# <a name="set-radix-command"></a>Команда Set Radix
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Задает или возвращает числовой базовый тип, используемый для отображения целочисленных значений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## <a name="arguments"></a>Аргументы  
 `10` или `16` или `hex` или `dec`  
 Необязательный параметр. Указывает десятичную (10 или dec) или шестнадцатеричную (16 или hex) систему счисления. Если аргумент отсутствует, возвращается основание текущей системы счисления.  
  
## <a name="example"></a>Пример  
 В приведенном примере в среде настраивается отображение целочисленных значений в шестнадцатеричном формате.  
  
```  
>Debug.SetRadix hex  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
