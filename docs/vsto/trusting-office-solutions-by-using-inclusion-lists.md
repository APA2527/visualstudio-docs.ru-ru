---
title: Доверять решениям Office с помощью списков включения
description: Узнайте, как списки включения позволяют пользователям предоставлять доверие решениям Office, подписанным с помощью сертификата, идентифицирующего издателя.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3bb5c111b4c75298ee55bc64dfbb2d0dd4b6c8b5
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527471"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Доверять решениям Office с помощью списков включения
  С помощью списков включений пользователи могут предоставлять доверие решениям Office, подписанным сертификатом, который идентифицирует издателя. Списки включений зависят от конкретного пользователя, и они могут использоваться для настроек уровня документа и надстроек VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Когда пользователь запускает решение Office, которому не было предоставлено доверие, решение Microsoft Office предлагает этому пользователю принять решение, влияющее на безопасность, в виде запроса о доверии [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Если пользователь решает доверять этому решению, настройка запускается, и в следующий раз пользователю не будет выдаваться запрос о доверии.

## <a name="inclusion-list-and-windows-installer"></a>Список включения и установщик Windows
 Для установки решений Office в каталог *Program Files* с помощью установщик Windows требуются права администратора. Для решений Office в каталоге *Program Files* среда выполнения инструменты Visual Studio для Office больше не проверяет список включения, так как решениям Office уже предоставлены разрешения FullTrust.

## <a name="clickonce-trust-prompt"></a>Запрос о доверии ClickOnce
 С помощью реализации [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] для решений Office администраторы могут настроить уровень запроса о доверии, чтобы разрешить запрос, отключить запрос или требовать надежный сертификат. Эта настройка выполняется с помощью раздела реестра, который управляет доступом к списку включений.

 Если запросы отключены, можно устанавливать только решения, имеющие надежный и известный сертификат. Если для уровня запросов установлено требование Authenticode, решение должно быть подписано сертификатом из известного центра, но сертификат, связанный с доверенным корневым центром (доверенный сертификат), не требуется. Если запрос разрешен, решение может быть подписано сертификатом с неизвестным удостоверением. В этом случае решение о доверии перекладывается на конечного пользователя, и для установки решения будет достаточно временного сертификата.

 Дополнительные сведения см. в разделе [как настроить безопасность списка включений](../vsto/how-to-configure-inclusion-list-security.md) и таблицу 2 с заголовком запуск значения раздела реестра уровня запроса в разделе [Настройка доверенных издателей ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="structure-of-the-inclusion-list"></a>Структура списка включения
 Правильная запись в списке включений состоит из двух частей: пути к манифесту развертывания и открытого ключа, используемого для подписи решения. После добавления решения в список включений оно считается доверенным. При запуске решения Office приложение Office сравнивает открытый ключ в списке включений с ключом подписывания в манифесте развертывания для проверки, что запущенное решение совпадает с исходной доверенной версией.

## <a name="see-also"></a>См. также раздел
- [Предоставление доверия решениям Office](../vsto/granting-trust-to-office-solutions.md)
- [Безопасные решения Office](../vsto/securing-office-solutions.md)
