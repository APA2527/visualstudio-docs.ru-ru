---
title: Сериализация сведений о символах | Документация Майкрософт
description: Сведения о том, как выполнить сериализацию символов,необходимых для анализа работы приложения, а также о способе, с помощью которого сериализация символов добавляет символы в VSP-файл.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b7cdfa6e64380c966b62d6691f73719a3034e2d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722091"
---
# <a name="how-to-serialize-symbol-information"></a>Практическое руководство. Сериализация сведений о символах
Можно выполнить сериализацию символов, необходимых для анализа работы приложения. При сериализации символы добавляются в *VSP*-файл. Если вы добавите сведения о символах в *VSP*-файл, другие пользователи смогут анализировать отчет о производительности без доступа к исходным символам. Если символы не сериализованы, для анализа *VSP*-файла необходимо иметь исходные инструментированные *EXE*- и *PDB*-файлы.

### <a name="to-automatically-serialize-symbol-information"></a>Автоматическая сериализация сведений о символах

1. В меню **Сервис** выберите пункт **Параметры**.

     Откроется диалоговое окно **Параметры**.

2. Щелкните **Средства производительности**.

3. В разделе **Общие параметры** выберите **Автоматическая сериализация символьной информации**.

## <a name="see-also"></a>См. также
- [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)
- [Практическое руководство. Справочная информация о символах Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [Практическое руководство. Сохранение файлов проанализированного отчета](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
