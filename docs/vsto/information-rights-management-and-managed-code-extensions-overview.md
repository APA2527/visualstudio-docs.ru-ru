---
title: Управление правами & расширения управляемого кода
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ca8f9d77681e3f11312e5e908a58ac2e292f581b
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177753"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Управление правами и общие сведения о расширениях управляемого кода
  Microsoft Office Word и Microsoft Office Excel предоставляют управления правами (IRM), это функция, которая может помочь предотвратить несанкционированного просмотра и изменения конфиденциальной информации. Дополнительные сведения о том, как работает управление правами см.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>Выполните код программной части документов с ограниченными разрешениями
 Если решение содержит документ или книгу, IRM, по умолчанию, Word и Excel не допускают выполнение кода. Если вы являетесь автором документа или иметь полный доступ, можно изменить значение по умолчанию, что решение. Дополнительные сведения см. в разделе [Практическое руководство. Разрешить выполнения кода программной части документов с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

 IRM не позволяет <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> для извлечения или управления данными, которые кэшируются в документе.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Конечным пользователям отменять разрешения для документов с помощью расширений управляемого кода
 Любой пользователь, у кого есть полный доступ к документу или книге в решении можно использовать IRM для ограничения разрешений. Например если конечный пользователь в бухгалтерии использует решение, которое автоматически заполняет лист с данными из базы данных, этот пользователь может потребоваться разрешить изменить доступ только к сотрудникам своего отдела и другим пользователям доступ на чтение. Когда пользователь добавляет ограниченные разрешения, по умолчанию не может выполняться кода программной части листа и листа не заполняется данными.

 Чтобы исправить эту проблему, кто-то доступа к документу или книге необходимо изменить настройки разрешений по умолчанию, обеспечивающие программный доступ к объектной модели. Дополнительные сведения см. в разделе [Практическое руководство. Разрешить выполнения кода программной части документов с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

## <a name="see-also"></a>См. также
- [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)
- [Защита паролей в документах Office](../vsto/password-protection-on-office-documents.md)
- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
