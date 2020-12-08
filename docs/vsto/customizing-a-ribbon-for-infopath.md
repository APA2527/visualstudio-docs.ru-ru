---
title: Настройка ленты для InfoPath
description: Сведения о том, что при настройке ленты в Microsoft Office InfoPath необходимо учитывать, где в приложении будет отображаться пользовательская лента.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: baf5a7edbdd9452c4b7ce55e109eee9c79798b5e
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844171"
---
# <a name="customize-a-ribbon-for-infopath"></a>Настройка ленты для InfoPath
  При настройке ленты в Microsoft Office InfoPath необходимо знать, где в приложении отображается пользовательская лента. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] может отображать ленту в окнах приложения InfoPath следующих трех типов.

- Окна, отображающие шаблон формы, открытый в режиме конструктора.

- Окна, отображающие форму, созданную на основе шаблона формы.

- Окно предварительного просмотра перед печатью.

  **Применимость.** Информация в этой статье относится к проектам надстроек VSTO для InfoPath 2010. Дополнительные сведения см. в разделе [доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).

  Пользователи и разработчики открывают шаблон формы в режиме конструктора, чтобы изменить внешний вид и макет шаблона. Пользователи открывают формы, созданные на основе шаблона формы, для добавления содержимого.

  Окно предварительного просмотра перед печатью позволяет разработчикам и пользователям просмотреть страницы формы или шаблона формы на экране перед тем, как отправить их на печать.

> [!NOTE]
> Вкладка **Надстройки** не отображается в окне предварительного просмотра перед печатью. Если вы хотите, чтобы пользовательская вкладка отображалась в окне предварительного просмотра, убедитесь, что для свойства **OfficeId** вкладки не задано значение **TabAddIns**.

 Необходимо указать тип ленты для каждого окна, в котором лента должна отображаться.

## <a name="specify-the-ribbon-type-in-the-ribbon-designer"></a>Указание типа ленты в конструкторе ленты
 Если вы используете элемент **Лента (визуальный конструктор)** , щелкните свойство **RibbonType** ленты в окне **Свойства** , а затем выберите любой идентификатор ленты, описанный в следующей таблице.

|Идентификатор ленты|Окно, в котором будет отображаться лента при выполнении проекта|
|---------------|---------------------------------------------------------------------|
|**Microsoft.InfoPath.Designer**|Окна, отображающие шаблон формы, открытый в режиме конструктора.|
|**Microsoft.InfoPath.Editor**|Окна, отображающие форму, созданную на основе шаблона формы.|
|**Microsoft.InfoPath.PrintPreview**|Окно предварительного просмотра перед печатью.|

 В проект можно добавить несколько лент. Если несколько лент имеют одинаковый идентификатор, переопределите метод `CreateRibbonExtensibilityObject` в классе `ThisAddin` проекта, чтобы указать, какую ленту следует отображать во время выполнения. Дополнительные сведения см. в статье [Общие сведения о ленте](../vsto/ribbon-overview.md).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Указание типа ленты с помощью XML-ленты
 Если вы используете элемент **Лента (XML)** , проверьте значение параметра *ribbonID* в методе <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> и верните нужную ленту.

 Метод <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> автоматически создается средой Visual Studio в файле кода ленты. Параметр *ribbonID* представляет собой строку, определяющую тип открываемого окна InfoPath.

 В следующем примере кода показано, как отобразить пользовательскую ленту только в том окне, которое отображает шаблон формы в режиме конструктора. Отображаемая лента указывается в методе `GetResourceText()` , который создается в классе ленты. Дополнительные сведения о классе Ribbon см. в разделе [Ribbon XML](../vsto/ribbon-xml.md).

 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]

## <a name="see-also"></a>См. также раздел
- [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)
- [Общие сведения о ленте](../vsto/ribbon-overview.md)
- [Конструктор ленты](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
