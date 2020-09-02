---
title: Загрузка вспомогательной сборки по запросу с помощью ClickOnce Designer
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f510ef4ad81188997e1d572e7aa3b52b65883269
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "66263405"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Пошаговое руководство. Загрузка вспомогательных сборок по требованию с помощью API развертывания ClickOnce в конструкторе
Приложения Windows Forms можно настроить для нескольких языков и региональных параметров, воспользовавшись вспомогательными сборками. *Вспомогательная сборка* — это сборка, содержащая ресурсы приложения для языка, отличного от языка и региональных параметров приложения по умолчанию.

 Как обсуждалось в разделе [локализация приложений ClickOnce](../deployment/localizing-clickonce-applications.md), можно включить несколько вспомогательных сборок для нескольких языков и региональных параметров в одном [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывании. По умолчанию [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] загружает все вспомогательные сборки в развертывание на клиентском компьютере, хотя один клиент, вероятно, потребует только одну вспомогательную сборку.

 Это пошаговое руководство показывает, как пометить вспомогательные сборки как необязательные и загрузить только сборку, необходимую клиентскому компьютеру для текущих настроек языка и региональных параметров.

> [!NOTE]
> В целях тестирования в следующих примерах кода программным образом задается следующий язык и региональные параметры: `ja-JP`. В подразделе «Дальнейшие действия» далее в этом разделе приводятся сведения о том, как настроить этот код для производственной среды.

### <a name="to-mark-satellite-assemblies-as-optional"></a>Как пометить вспомогательные сборки как необязательные

1. Построить проект. Это позволяет создать вспомогательные сборки для всех языков и региональных параметров, для которых выполняется локализация.

2. Щелкните правой кнопкой мыши имя проекта в обозревателе решений и выберите **Свойства**.

3. Перейдите на вкладку **Опубликовать** и нажмите кнопку **Файлы приложения**.

4. Установите флажок **Показать все файлы**, чтобы отобразить вспомогательные сборки. По умолчанию все вспомогательные сборки будут включены в развертывание и будут видны в этом диалоговом окне.

     Вспомогательная сборка будет иметь имя в форме * \<isoCode>\ApplicationName.resources.dll*, где \<isoCode> — идентификатор языка в формате RFC 1766.

5. Щелкните **Создать** в списке **Группа загрузки** для каждого идентификатора языка. При появлении запроса имени группы загрузки введите идентификатор языка. Например, для японской вспомогательной сборки необходимо указать имя группы загрузки `ja-JP` .

6. Закройте диалоговое окно **Файлы приложения**.

### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>Загрузка вспомогательных сборок по требованию в C\#

1. Откройте файл *Program.cs*. Если вы не видите этот файл в обозревателе решений, выберите проект и в меню **Проект** щелкните **Показать все файлы**.

2. Используйте следующий код для загрузки соответствующей вспомогательной сборки и запуска приложения.

     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]

### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Загрузка вспомогательных сборок по требованию в Visual Basic

1. В окне **Свойства** для приложения щелкните вкладку **Приложение**.

2. В нижней части вкладки нажмите кнопку **Просмотреть события приложения**.

3. Добавьте следующие операции импорта в начало файла *ApplicationEvents. vb* .

     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]

4. Добавьте в класс `MyApplication` приведенный далее код.

     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]

## <a name="next-steps"></a>Дальнейшие действия
 В продуктивной среде, скорее всего, потребуется удалить строку в примерах кода, задающую определенное значение для свойства <xref:System.Threading.Thread.CurrentUICulture%2A>, потому что на клиентских компьютерах правильное значение будет задаваться по умолчанию. Если приложение выполняется на клиентском компьютере с японским языком, например, свойство <xref:System.Threading.Thread.CurrentUICulture%2A> будет по умолчанию равно `ja-JP` . Программная установка этого значения — хороший способ проверить вспомогательные сборки перед развертыванием приложения.

## <a name="see-also"></a>См. также раздел
- [Пошаговое руководство. Загрузка вспомогательных сборок по требованию с помощью API развертывания ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)
- [Локализация приложений ClickOnce](../deployment/localizing-clickonce-applications.md)
