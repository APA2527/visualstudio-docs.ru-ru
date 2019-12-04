---
title: Параметр Events (VSPerfCmd) | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 46b47f9b615c824d25e931cd3d05f5d2a04257ba
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777325"
---
# <a name="events-vsperfcmd"></a>Параметр Events (VSPerfCmd)
Параметр **Events** программы *VSPerfCmd.exe* позволяет управлять ведением журнала трассировки событий Windows. Данные трассировки событий Windows сохраняются в ETL-файле, который отличается от файла данных профилировщика. Эти данные можно просмотреть в отчете с помощью команды [VSPerfReport](../profiling/vsperfreport.md) /summary:etw.

 Параметр **Events** можно использовать в любой момент перед вызовом команды **Shutdown** программы VSPerfCmd для остановки профилирования.

## <a name="syntax"></a>Синтаксис

```cmd
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]
```

#### <a name="parameters"></a>Параметры
 **On**&#124;**Off** запускает или останавливает сбор данных события.

 `Guid` Идентификатор GUID элемента управления поставщика.

 `ProviderName` Имя поставщика, созданного с помощью инструментария управления Windows (WMI).

 `Flags` Значение флагов с префиксом "0x", заданное поставщиком событий.

 `Level` Задает объем собираемых данных. `Level` определяется поставщиком событий.

 Параметр **Events** распознает в качестве имен поставщиков перечисленные ниже ключевые слова ядра.

 **Process**. События процесса

 **Thread**. События потоков

 **Image**. События загрузки и выгрузки образов

 **Disk**. События ввода-вывода на диске

 **File**. События ввода-вывода в файле

 **Hardfault**. Ошибки страниц физической памяти

 **Pagefault**. Ошибки страниц, подготовленных к просмотру

 **Network**. Сетевые события

 **Registry**. События доступа к реестру

 Необходимо заметить, что Kernel Provider можно только включить. До завершения работы монитора невозможно отключить этот поставщик или изменить его флаги.

## <a name="remarks"></a>Примечания

> [!NOTE]
> При возникновении событий трассировки событий Windows среды CLR для отчета представления трассировки собираются также дополнительные сведения о запуске. Чтобы исключить события запуска из отчета, используйте следующую команду:

```cmd
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5
```

> [!IMPORTANT]
> Так как события запуска не перечислены в MOF-файле, то если их не исключить, они отображаются в отчете в виде идентификаторов GUID. Дополнительные сведения см. на странице [Образец MOF-файла](https://msdn.microsoft.com/library/default.aspx) веб-сайта корпорации Майкрософт.

## <a name="see-also"></a>См. также
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Профилирование служб](../profiling/command-line-profiling-of-services.md)
