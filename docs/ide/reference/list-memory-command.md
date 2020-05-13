---
title: Команда List Memory
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c500b1b516c2b1ab1bc66b7970fccc4ec7a85baa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568715"
---
# <a name="list-memory-command"></a>Команда List Memory
Отображает содержимое указанного диапазона памяти.

## <a name="syntax"></a>Синтаксис

```cmd
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Аргументы
`expression`

Необязательный параметр. Адрес памяти, с которого начинается отображение памяти.

## <a name="switches"></a>Коммутаторы
/ANSI&#124;Unicode

Необязательный параметр. Отображает память в виде символов, соответствующих байтам памяти, в формате ANSI или Юникод.

/Count:`number`

Необязательный параметр. Определяет, сколько байт памяти нужно отобразить, начиная с `expression`.

/Format:`formattype`

Необязательный параметр. Тип формата для просмотра данных памяти в окне **Память**, может иметь значение OneByte, TwoBytes, FourBytes, EightBytes, Float (32-разрядный) или Double (64-разрядный). При использовании OneByte параметр `/Unicode` недоступен.

/Hex&#124;Signed&#124;Unsigned

Необязательный параметр. Указывает формат для просмотра чисел: со знаком, без знака или в шестнадцатеричном формате.

## <a name="remarks"></a>Remarks
Вместо записи полной команды **Debug.ListMemory** со всеми параметрами можно вызвать ее, используя стандартные псевдонимы, в которых отдельные параметры уже имеют определенные значения. Например, вместо ввода:

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

можно ввести:

```cmd
>df /Count:30 /Unicode
```

Ниже приведен список доступных псевдонимов для команды **Debug.ListMemory**:

|Псевдоним|Команда и параметры|
|-----------| - |
|**d**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**db**|Debug.ListMemory /Format:OneByte|
|**dc**|Debug.ListMemory /Format:FourBytes /Ansi|
|**дд**|Debug.ListMemory /Format:FourBytes|
|**df**|Debug.ListMemory /Format:Float|
|**dq**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a>Пример

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>См. также раздел

- [Команда "Вывести стек вызовов"](../../ide/reference/list-call-stack-command.md)
- [Команда "Вывести потоки"](../../ide/reference/list-threads-command.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Окно команд](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
