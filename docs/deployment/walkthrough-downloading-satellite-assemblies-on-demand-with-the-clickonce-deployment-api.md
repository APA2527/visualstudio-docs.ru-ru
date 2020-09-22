---
title: Скачать вспомогательную сборку по требованию (API ClickOnce)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cda69b1aad8e70dce14bb3f25e6bf935103642bf
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809241"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Пошаговое руководство. Загрузка вспомогательных сборок по требованию с помощью API развертывания ClickOnce
Приложения Windows Forms можно настроить для нескольких языков и региональных параметров, воспользовавшись вспомогательными сборками. *Вспомогательная сборка* — это сборка, содержащая ресурсы приложения для языка, отличного от языка и региональных параметров приложения по умолчанию.

 Как обсуждалось в разделе [локализация приложений ClickOnce](../deployment/localizing-clickonce-applications.md), можно включить несколько вспомогательных сборок для нескольких языков и региональных параметров в одном [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывании. По умолчанию [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] загружает все вспомогательные сборки в развертывание на клиентском компьютере, хотя один клиент, вероятно, потребует только одну вспомогательную сборку.

 Это пошаговое руководство показывает, как пометить вспомогательные сборки как необязательные и загрузить только сборку, необходимую клиентскому компьютеру для текущих настроек языка и региональных параметров. В следующей процедуре используются средства, доступные в [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Эту задачу также можно выполнить в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  См. также раздел [Пошаговое руководство. скачивание вспомогательных сборок по запросу с помощью API развертывания ClickOnce в конструкторе](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) или [пошаговом руководстве: скачивание вспомогательных сборок по запросу с помощью API развертывания ClickOnce с использованием конструктора](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).

> [!NOTE]
> В целях тестирования в следующем примере кода программным образом задается следующий язык и региональные параметры: `ja-JP`. В подразделе «Дальнейшие действия» далее в этом разделе приводятся сведения о том, как настроить этот код для производственной среды.

## <a name="prerequisites"></a>Предварительные требования
 Составители этого раздела исходили из того, что вы знаете, как добавить локализованные ресурсы в свое приложение с использованием Visual Studio. Подробные инструкции см. в разделе [Пошаговое руководство. Локализация Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100)).

### <a name="to-download-satellite-assemblies-on-demand"></a>Загрузка вспомогательных сборок по требованию

1. Добавьте следующий код в приложение, чтобы включить загрузку вспомогательных сборок по требованию.

    [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
    [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]

2. Создайте вспомогательные сборки для приложения с помощью [Resgen.exe (генератор файлов ресурсов)](/dotnet/framework/tools/resgen-exe-resource-file-generator) или [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

3. Создайте манифест приложения или откройте существующий манифест приложения с помощью *MageUI.exe*. Дополнительные сведения об этом средстве см. в разделе [MageUI.exe (инструмент создания и изменения манифестов, графический клиент)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

4. Щелкните вкладку **Файлы** .

5. Нажмите кнопку **с многоточием** (**...**) и выберите каталог, содержащий все сборки и файлы приложения, включая вспомогательные сборки, созданные с помощью *Resgen.exe*. (Вспомогательная сборка будет иметь имя в форме * \<isoCode>\ApplicationName.resources.dll*, где \<isoCode> — идентификатор языка в формате RFC 1766.)

6. Щелкните **Заполнить** , чтобы добавить файлы в ваше развертывание.

7. Установите флажок **Необязательно** для каждой вспомогательной сборки.

8. Установите в поле группировки для каждой вспомогательной сборки соответствующий идентификатор языка по ISO. Например, для японской вспомогательной сборки нужно указать имя группы загрузки `ja-JP`. В результате код, добавленный вами в шаге 1, сможет загружать соответствующую вспомогательную сборку в зависимости от настройки свойства <xref:System.Threading.Thread.CurrentUICulture%2A> у пользователя.

## <a name="next-steps"></a>Дальнейшие действия
 В продуктивной среде, скорее всего, потребуется удалить строку в примере кода, задающую определенное значение для свойства <xref:System.Threading.Thread.CurrentUICulture%2A> , потому что на клиентских компьютерах правильное значение будет задаваться по умолчанию. Если приложение выполняется на клиентском компьютере с японским языком, например, свойство <xref:System.Threading.Thread.CurrentUICulture%2A> будет по умолчанию равно `ja-JP` . Программная установка этого значения — хороший способ проверить вспомогательные сборки перед развертыванием приложения.

## <a name="see-also"></a>См. также раздел
- [Локализация приложений ClickOnce](../deployment/localizing-clickonce-applications.md)
