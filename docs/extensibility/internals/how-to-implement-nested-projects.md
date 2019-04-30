---
title: Практическое руководство. Реализация вложенных проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96df14cc6e337402761d89d7161094b513473a78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62860767"
---
# <a name="how-to-implement-nested-projects"></a>Практическое руководство. Реализация вложенных проектов

При создании проекта, вложенного типа, существует несколько дополнительных шагов, которые должны быть реализованы. На некоторых те же обязанности, решение содержит его проектов вложенные (дочерние) принимает родительского проекта. Родительский проект — это контейнер, аналогичную решения проектов. В частности есть несколько событий, которые должны вызываться в решении и родительские проекты для построения иерархии вложенных проектов. Эти события описаны в процесс для создания вложенных проектов.

## <a name="create-nested-projects"></a>Создание вложенных проектов

1. Интегрированной среде разработки (IDE) загружает сведения о файлах и запуска проекта в родительский проект путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> интерфейс. Родительский проект создается и добавляется в решение.

    > [!NOTE]
    > На этом этапе является слишком ранним процесса для родительского проекта для создания вложенных проектов, так как перед созданием дочерние проекты должны создаваться в родительский проект. Следующую последовательность в родительский проект можно применить параметры в дочерние проекты, и дочерние проекты можно получить сведения из родительской проектов, при необходимости. Эта последовательность является, если он необходим для клиентов, таких как системы управления исходным кодом (SCC) и **обозревателе решений**.

     Родительский проект необходимо дождаться <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> метод вызывается в интегрированной среде разработки до ее можно создать его вложенные (дочерние), или проектов.

2. Интегрированная среда разработки вызовы `QueryInterface` на родительский проект для <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>. Если этот вызов выполняется успешно, вызовы IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> метод родительского элемента для открытия всех вложенных проектов для родительского проекта.

3. Вызовы родительского проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> метод для уведомления прослушивателей, вложенные проекты должны создаваться. SCC, например, ожидает передачи данных на эти события, чтобы знать, если действия, описанные в процесс создания проектов и решений выполняются в порядке. Если шаги по порядку, решение может не зарегистрирована с контролем исходного кода.

4. Вызовы родительского проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> метод или <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> метод на каждом из его дочерних проектов.

     Вы передаете <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> для `AddVirtualProject` добавляемый метод, чтобы указать, что виртуальный проект (вложенная) должны быть добавлены в окно проекта, исключено из сборки, управления исходным кодом и т. д. `VSADDVPFLAGS` позволяет управлять видимостью вложенного проекта и указать, какие функциональные возможности, связанные с ним.

     Если вы перезагрузите ранее существующий дочерний проект с GUID, хранимое в файле проекта родительский проект, вызываемого проектом родительского проекта `AddVirtualProjectEx`. Единственное различие между `AddVirtualProject` и `AddVirtualProjectEX` является то, что `AddVirtualProjectEX` имеет параметр для включения в родительский проект указать на один экземпляр `guidProjectID` для дочернего проекта включить <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> функции правильно.

     Если есть идентификатор GUID не доступны, например при добавлении нового вложенного проекта, решение создает один для проекта во время он добавляется в родительский объект. Он отвечает родительского проекта для сохранения этого проекта GUID в файле проекта. При удалении вложенного проекта, можно также удалить идентификатор GUID для этого проекта.

5. Интегрированная среда разработки вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> метод для каждого дочернего проекта родительского проекта.

     Родительский проект должен реализовывать `IVsParentProject` Если вы хотите вкладывать друг в друга проектов. Но родительский проект никогда не вызывает `QueryInterface` для `IVsParentProject` даже если он имеет родительские проекты под ним. Решение выполняет вызов `IVsParentProject` и, если оно реализовано, вызывает `OpenChildren` для создания вложенных проектов. `AddVirtualProjectEX` всегда вызывается из `OpenChildren`. Он никогда не должен вызываться с родительского проекта для сохранения события создания иерархии в порядке.

6. Интегрированная среда разработки вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> метод дочернему проекту.

7. Вызовы родительского проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> метод для уведомления прослушивателей, что были созданы дочерние проекты для родительского элемента.

8. Интегрированная среда разработки вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> метод на родительский проект после открытия всех дочерних проектов.

     Если он еще не существует, в родительский проект создает идентификатор GUID для каждого вложенного проекта путем вызова `CoCreateGuid`.

    > [!NOTE]
    > `CoCreateGuid` вызывается при GUID создаваемого COM API. Дополнительные сведения см. в разделе `CoCreateGuid` и идентификаторы GUID в библиотеке MSDN.

     Родительский проект сохраняет этот GUID в его файле проекта, извлекаемых в следующий раз, то он открывается в интегрированной среде разработки. См. в шаге 4, Дополнительные сведения, относящиеся к вызовы `AddVirtualProjectEX` извлекаемого `guidProjectID` для дочернего проекта.

9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Затем вызывается метод для ItemID родительского по соглашению делегировать в для вложенного проекта. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Извлекает свойства, вложенной в проект, который нужно передать в, когда он вызывается для родительского узла.

     Так как родительские и дочерние проекты создаются программным образом, можно задать свойства для вложенных проектов на этом этапе.

    > [!NOTE]
    > Не только получаете контекстную информацию из вложенного проекта, но также можно задать, если родительский проект имеет любой контекст для этого элемента путем проверки [__VSHPROPID. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). Таким образом можно добавить атрибуты очень динамическую справку и определенные параметры меню в отдельные вложенные проекты.

10. Иерархия создается для отображения в **обозревателе решений** вызовом <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> метод.

     Передать иерархии в среде с помощью `GetNestedHierarchy` для построения иерархии для отображения в обозревателе решений. Таким образом решение знает, что проект существует и диспетчером построения можно управлять для создания или можно разрешить файлов в проекте, которые требуется поместить в систему управления версиями.

11. После создания всех вложенных проектов для Project1 управление передается в решение, и этот процесс повторяется для Project2.

     Аналогичным образом для создания вложенных проектов выполняется для дочернего проекта, имеющие дочерние объекты. В этом случае если BuildProject1, который является потомком Project1, дочерние проекты, они будут создаваться после BuildProject1 и перед (Project2). Является рекурсивным и иерархии строится сверху вниз.

     При закрытии вложенного проекта, так как пользователь закрыл решение или проект конкретный, самого другой метод в `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, вызывается. Родительский проект служит оболочкой для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> метод с <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> методы для уведомления прослушивателей событий решения закрытие вложенных проектов.

Следующие разделы имеют дело с несколько других понятиях, которые следует учитывать при реализации вложенных проектов:

- [Рекомендации по выгрузке и перезагрузке вложенных проектов](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Поддержка мастера для вложенных проектов](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Реализация обработки команд для вложенных проектов](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Фильтрация диалогового окна AddItem для вложенных проектов](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>См. также

- [Добавление элементов в диалоговом окне Добавление нового элемента](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)
- [Контрольный список. Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Контекстные параметры](../../extensibility/internals/context-parameters.md)
- [Файл мастера (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)