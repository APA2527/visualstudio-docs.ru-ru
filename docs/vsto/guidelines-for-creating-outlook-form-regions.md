---
title: Рекомендации по созданию областей формы Outlook
description: Узнайте о рекомендациях по созданию областей форм Outlook, которые помогут оптимизировать области формы и избежать потенциальных проблем.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a3a2fab671d6302583f1207f5756118c548bd8a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933613"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Рекомендации по созданию областей формы Outlook
  Следующие сведения помогут вам оптимизировать области формы и предотвращать потенциальные проблемы.

- [Используйте имена областей формы](#UsingFormRegions).

- [Отключить наследование области формы](#DisablingInheritance).

- [Общие сведения о типах и именах классов сообщений](#ClassNames).

- [Разработка смежных областей формы для панели чтения](#ReadingPane).

- [Используйте оптимальные размеры значков](#UsingOptimal).

  Дополнительные сведения о регионах форм см. в разделе [Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md).

  [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="use-form-region-names"></a><a name="UsingFormRegions"></a> Использование имен областей формы
 Существует несколько имен, используемых для описания области формы. Важно понимать разницу между этими именами и то, как они влияют на область формы. В следующей таблице представлено описание этих имен.

|Имя области формы|Описание|
|----------------------|-----------------|
|Имя элемента области формы|Имя, заданное для элемента **Область формы Outlook** в диалоговом окне **Добавление нового элемента** . Это имя файла кода области формы, которое отображается в **обозревателе решений**.|
|Свойство<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A>|Вы указываете это имя на странице **Введите текст описания и выберите параметры отображения** мастера **создания области формы Outlook** . Оно отображается как свойство **FormRegionName** в окне **Свойства** .<br /><br /> Используйте свойство <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> , чтобы указать метку, идентифицирующую область формы в пользовательском интерфейсе Outlook. Для отдельных областей формы это имя отображается в виде кнопки на ленте элемента Outlook.<br /><br /> Для соседних областей формы это имя отображается в заголовке над областью формы.|
|Атрибут `Microsoft.Office.Tools.Outlook.FormRegionName`|При добавлении в проект Visual Studio элемента **Область формы Outlook** Visual Studio задает в качестве значения этого свойства полное имя области формы. Полное имя по умолчанию — это имя надстройки VSTO, присоединенное к имени области формы через точку, например, `OutlookAddIn1.FormRegion1`.<br /><br /> Это полное имя также отображается как атрибут в верхней части класса фабрики областей формы.<br /><br /> Используйте `Microsoft.Office.Tools.Outlook.FormRegionName` атрибут, чтобы уникальным образом идентифицировать область формы для всех надстроек VSTO Outlook. Значение атрибута нельзя изменить `Microsoft.Office.Tools.Outlook.FormRegionName` , переименовав элемент области формы или изменив <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> свойство. Чтобы изменить это имя, необходимо изменить атрибут `Microsoft.Office.Tools.Outlook.FormRegionName` в файле кода области формы.|

## <a name="disable-form-region-inheritance"></a><a name="DisablingInheritance"></a> Отключить наследование области формы
 По умолчанию специализированный класс сообщений наследует все связи областей формы базового класса сообщений. Например, класс сообщений с именем `IPM.Task.Contoso` является производным от `IPM.Task`. Таким образом, `IPM.Task.Contoso` наследует связи областей формы `IPM.Task`.

 Если вы не хотите, чтобы область формы была связана с каким-либо производным классом сообщений, установите для свойства <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> области формы значение **true**. Например, если связать смежную область формы с `IPM.Task` и установить <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> для свойства **значение true**, то область формы будет добавлена только в нижнюю часть формы стандартной задачи. Эта область формы не будет добавлена ни к каким настраиваемым версиям стандартной формы задач.

## <a name="understand-types-and-message-class-names"></a><a name="ClassNames"></a> Общие сведения о типах и именах классов сообщений
 Имя типа элемента Outlook отличается от имени класса сообщений для элемента Outlook. Например, имя типа элемента RSS — `Microsoft.Office.Interop.Outlook.PostItem`. Имя класса сообщений для элемента RSS — `IPM.Post.RSS`.

 Используйте имя типа для ссылки на элемент Outlook в коде. Список имен типов см. в разделе [Связывание области формы с классом сообщений Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

 Используйте имя класса сообщений элемента Outlook в мастере **создания области формы Outlook** , чтобы связать этот элемент с областью формы. Список допустимых имен классов сообщений см. в разделе [Связывание области формы с классом сообщений Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="design-adjoining-form-regions-for-the-reading-pane"></a><a name="ReadingPane"></a> Проектирование смежных областей формы для панели чтения
 Область чтения Outlook можно использовать для предварительного просмотра элемента Outlook без его открытия. Область чтения предназначена только для чтения. Таким образом, элементы управления для ввода, добавляемые в смежную область формы, например текстовое поле, могут работать некорректно при открытии элемента и области формы в области чтения.

 Например, если в области чтения открыт элемент, имеющий смежную область формы, возможна следующая ситуация.

1. Выберите какой-либо текст в текстовом поле, которое находится в области формы.

2. Нажмите клавишу **Delete**.

3. Вместо текста в текстовом поле удаляется все сообщение.

   При конструировании смежной области формы, содержащей элементы управления для ввода, тестируйте эти элементы управления в области чтения, чтобы убедиться, что они работают правильно. Рассмотрите возможность добавления пользовательского кода, который отключает элементы управления, не работающие должным образом.

   Можно также задать для свойства <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> области формы значение **False**. Тогда эту область формы нельзя будет использовать в области чтения.

## <a name="use-optimal-icon-sizes"></a><a name="UsingOptimal"></a> Использовать оптимальные размеры значков
 Вы можете указывать, какие значки должны отображаться в области формы, задавая свойства значков в группе свойств **Значки** окна **Свойства** . Для достижения наилучшего визуального качества следуйте приведенным ниже рекомендациям.

- Для значка **Страница** используйте файл формата PNG.

- Значки **Окно** должны иметь размер 32 на 32 пикселя.

- Все остальные значки должны иметь размер 16 на 16 пикселей.

  Значок **Страница** появляется в ленте инспектора для элементов, имеющих области формы "Разделить", "Заменить" или "Заменить все".

  Значок **окна** отображается в области уведомлений и в диалоговом окне **ALT** на + **вкладке** для открытых элементов, в которых отображаются области замены или замены всех областей формы.

## <a name="see-also"></a>См. также раздел
- [Доступ к области формы во время выполнения](../vsto/accessing-a-form-region-at-run-time.md)
- [Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md)
- [Пошаговое руководство. Проектирование области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Как добавить область формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Связывание области формы с классом сообщений Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
