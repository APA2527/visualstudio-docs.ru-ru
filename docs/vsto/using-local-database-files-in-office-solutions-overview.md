---
title: Общие сведения об использовании файлов локальной базы данных в решениях Office
description: Узнайте, как можно включить файл базы данных, например файл SQL Server Express (MDF) или файл Microsoft Office Access (MDB) в решении Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 857038700a29f423250f006e743152bceea43c14
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838239"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Общие сведения об использовании файлов локальной базы данных в решениях Office
  В решение Office можно включить файл базы данных, например файл SQL Server Express (*MDF*) или файл Microsoft Office Access (*MDB*). Это позволяет конечным пользователям поддерживать локальную базу данных в ситуациях, когда не требуется обслуживать централизованную базу данных, например в решении локального учета, которое используется только на одном компьютере.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>Импорт файла базы данных в проект
 Чтобы импортировать файл базы данных в проект, используйте **Мастер настройки источника данных** , чтобы создать источник данных на основе файла базы данных. Мастер добавляет в проект файл базы данных и типизированный набор данных.

## <a name="deploy-the-database-file"></a>Развертывание файла базы данных
 **Мастер настройки источника данных** использует относительный путь для создания соединений с файлом локальной базы данных. Это позволяет копировать решение с одного компьютера на другой, если поддерживаются относительные положения файлов.

 При развертывании решения на сервере и последующем распространении документа для каждого конечного пользователя необходимо также вручную распространить файл базы данных и установить его в той же папке, что и документ. Это означает, что конечный пользователь не может переместить документ в новое место на своем компьютере, если он также не перемещает файл базы данных.

## <a name="local-database-files-and-caching-the-dataset"></a>Файлы локальной базы данных и кэширование набора данных
 В решениях на уровне документа для Microsoft Office Excel и Microsoft Office Word можно кэшировать наборы данных в документе, пометив экземпляр DataSet атрибутом <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> . При добавлении файла базы данных в проект с помощью **мастера настройки источника данных** типизированный набор данных добавляется в проект автоматически. Нередко требуется применять <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> к этому набору данных, так как данные уже являются локальными на компьютере пользователя. Дополнительные сведения см. в разделе [кэширование данных](../vsto/caching-data.md).

## <a name="see-also"></a>См. также раздел
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Как заполнить документы данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
- [Кэширование данных](../vsto/caching-data.md)
