---
title: Практическое руководство. Определение расположения файлов символов с помощью командной строки | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 01fbb6cfd1717562af79c067ede0cad9753ad5dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "77557895"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Практическое руководство. Определение расположения файлов символов с помощью командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для отображения сведений о символах, например имен функций и номеров строк, программе командной строки VSPerfReport необходим доступ к файлам символов (PDB) профилируемых компонентов и системным файлам Windows. Файлы символов создаются при компиляции компонента. Дополнительные сведения см. в разделе [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport автоматически выполняет поиск следующих расположений файлов символов:  
  
- пути, указанные в параметре **/SymbolPath** или в переменной среды **_NT_SYMBOL_PATH**;  
  
- точный локальный путь к папке, в которой был скомпилирован компонент;  
  
- каталог, содержащий файл данных профилирования (VSP или VSPS).  
  
  Корпорация Майкрософт предоставляет PDB-файлы для многих своих продуктов через Интернет на сервере символов. Если компьютер, используемой для создания отчетов, подключен к Интернету, программа VSPerfReport подключается к серверу символов по сети для автоматического поиска сведений о символах и сохранения файлов в локальном хранилище.  
  
  Расположение файлов символов и хранилища сервера символов Майкрософт можно указать следующим образом:  
  
- задайте переменную среды **_NT_SYMBOL_PATH**;  
  
- добавьте параметр **/SymbolPath** в командную строку VSPerfReport.  
  
  Можно также использовать оба этих метода.  
  
> [!NOTE]
> Если [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] установлен на локальном компьютере, расположение файлов символов Windows, вероятно, уже указано. Дополнительные сведения см. [в разделе руководство. справочные сведения о символах Windows](../profiling/how-to-reference-windows-symbol-information.md). Вам, тем не менее, потребуется настроить в VSPerfReport использование расположения и сервера, как описано далее в этом разделе.  
  
## <a name="specifying-windows-symbol-files"></a>Задание файлов символов Windows  
  
#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Настройка использования сервера символов Windows  
  
1. При необходимости создайте каталог для локального хранения файлов символов.  
  
2. Используйте следующий синтаксис для задания переменной среды **_NT_SYMBOL_PATH** или параметра VSPerfReport /SymbolPath:  
  
   `srv*<LocalStore>*https://msdl.microsoft.com/downloads/symbols`  
  
   где *<LocalStore>*  — путь созданного локального каталога.  
  
## <a name="specifying-component-symbol-files"></a>Задание файлов символов компонентов  
 Средства профилирования выполняют поиск PDB-файлов компонентов, которые требуется профилировать, в исходном расположении в компонентах или в папке, содержащей файл данных профилирования. Можно указать другие расположения для поиска, добавив один или несколько путей в переменную **_NT_SYMBOL_PATH** или в параметр **/SymbolPath**. Отделяйте пути точкой с запятой.  
  
## <a name="example"></a>Пример  
 Следующая командная строка задает в качестве переменной среды **_NT_SYMBOL_PATH** сервер символов Windows и **C:\Symbols** в качестве локального каталога.  

 ```cmd
 set  _NT_SYMBOL_PATH=srv*C:\symbols*https://msdl.microsoft.com/downloads/symbols
 ```

 Следующая командная строка VSPerfReport добавляет каталог C:\Projects\Symbols в путь поиска с помощью параметра **/SymbolPath**.  
  
 **VSPerfReport**  *MyApp* **.exe /SymbolPath:C:\Projects\Symbols /summary:all**
