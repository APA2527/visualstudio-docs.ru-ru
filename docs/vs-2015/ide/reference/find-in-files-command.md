---
title: Команда Find in Files | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 831a67fe567c2e6ae1e288d1bc7ee91026ff2273
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651027"
---
# <a name="find-in-files-command"></a>Команда Find in Files
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Поиск в файлах с использованием набора параметров, доступных на вкладке **Найти в файлах** диалогового окна **Поиск и замена**.

## <a name="syntax"></a>Синтаксис

```
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Аргументы
 `findwhat` Обязательный. Текст для поиска совпадения.

## <a name="switches"></a>Переключатели
 /case или /c Необязательный. Совпадение происходит только в том случае, если прописные и строчные знаки точно соответствуют тем, что указаны в аргументе `findwhat`.

 /ext: `extensions` Необязательный. Определяет расширения файлов, в которых будет проводиться поиск. Если переключатель не определен, используется предыдущее расширение, вводившееся ранее.

 /lookin: `searchpath` Необязательный. Каталог, в котором будет производиться поиск. Если путь содержит пробелы, необходимо заключить полный путь в кавычки.

 /names или /n Необязательный. Отображает список имен файлов, содержащих совпадения.

 /options или /t Необязательный. Отображает список текущих параметров поиска, но не выполняет сам поиск.

 /regex или /r Необязательный. Использует стандартные специальные символы в аргументе `findwhat` для представления текстовых шаблонов вместо самих букв. Полный список знаков регулярных выражений см. в разделе [Регулярные выражения](../../ide/using-regular-expressions-in-visual-studio.md).

 /reset или /e Необязательный. Для параметров поиска возвращает их значения по умолчанию, но не выполняет сам поиск.

 /stop Необязательный. Останавливает выполнение текущей активной операции поиска. Если указан аргумент `/stop`, остальные аргументы при поиске игнорируются. Например, чтобы остановить текущий поиск, следует ввести следующую строку:

```
>Edit.FindinFiles /stop
```

 /sub или /s Необязательный. Выполняет поиск в папках, вложенных в каталог, который указан в аргументе /lookin:`searchpath`.

 /text2 или /2 Необязательный. Отображает результаты поиска в окне "Результаты поиска 2".

 /wild или /l Необязательный. Использует стандартные специальные символы в аргументе `findwhat` для представления символа или последовательности символов.

 /word или /w Необязательный. Выполняет поиск только целых слов.

## <a name="example"></a>Пример
 В данном примере осуществляется поиск "btnCancel" во всех CLS-файлах, расположенных в папке My Visual Studio Projects, а в окне "Результаты поиска 2" отображаются сведения о найденных совпадениях.

```
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>См. также
 [Поиск в файлах](../../ide/find-in-files.md) [командное окно](../../ide/reference/command-window.md) [Найти/Команда](../../ide/find-command-box.md) Командная кнопка [Visual Studio команды](../../ide/reference/visual-studio-commands.md) Visual Studio [псевдонимы команд](../../ide/reference/visual-studio-command-aliases.md)
