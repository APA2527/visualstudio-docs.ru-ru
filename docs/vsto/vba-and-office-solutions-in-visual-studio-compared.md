---
title: Сравнение решений VBA и Office в Visual Studio
description: Сведения о различиях между решениями Microsoft Visual Basic для приложений (VBA) и Microsoft Office в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a07711fd854bd0dc035cab776f713701d5d85200
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838117"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Сравнение решений VBA и Office в Visual Studio
  В Microsoft Visual Basic для приложений (VBA) используется неуправляемый код, который тесно интегрирован с приложениями Office. Проекты Microsoft Office, созданные с помощью Visual Studio, позволяют воспользоваться преимуществами платформы .NET Framework и средств разработки Visual Studio.

 Сведения о типах решений Office, которые можно создать с помощью Visual Studio, см. в статье [Общие сведения о разработке решений office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="comparison"></a>Сравнение
 В следующей таблице приводится общее сравнение решений VBA и решений Office в Visual Studio.

|Решения VBA|Решения Office в Visual Studio|
|-------------------|---------------------------------------|
|Использует код, который связан с конкретным документом и сохраняется с ним.|Использует код, хранящийся отдельно от документа (для настроек на уровне документа) или в сборке, которая загружается приложением (для надстроек VSTO).|
|Работает с объектными моделями Office и программными интерфейсами VBA.|Предоставляет доступ к объектным моделям Office и API-интерфейсам [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|
|Предназначен для записи макросов и упрощения процесса разработки.|Предназначен для обеспечения безопасности, упрощения поддержки кода и использования полной интегрированной среды разработки (IDE) Visual Studio.|
|Подходит для решений, которые получают преимущества от тесной интеграции с приложениями Office.|Подходит для решений, которые получают преимущества от полных ресурсов Visual Studio и [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|
|Имеет ограничения при использовании на предприятиях, особенно в области безопасности и развертывания.|Предназначен для использования на предприятиях.|

 Некоторые задачи по-прежнему проще и быстрее выполнить с помощью VBA. В частности, VBA может быть необходимо использовать для:

- настраиваемых функций для работы с листами.

- записи макросов.

## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Объединение решений VBA и решений Office, созданных с помощью Visual Studio
 Код VBA можно вызывать из решений Office, созданных с помощью Visual Studio. Также можно вызывать код в решениях Office, созданных с помощью Visual Studio, из VBA. Конкретная методика зависит от того, является ли ваше решение Office надстройкой VSTO или настройкой на уровне документа. Дополнительные сведения см. в статьях [вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) и [Объединение настроек VBA и настройки на уровне документа](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="see-also"></a>См. также раздел
- [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Объединение настроек VBA и параметров на уровне документа](../vsto/combining-vba-and-document-level-customizations.md)
- [Архитектура настроек уровня документа](../vsto/architecture-of-document-level-customizations.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Приступая к работе &#40;разработке решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
