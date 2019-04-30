---
title: Вызов кода в надстройках VSTO из других решений Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5dbf56278a3987fafa0e0a0263c17460b56fafaf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939252"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>Вызов кода в надстройках VSTO из других решений Office
  Объект в надстройке VSTO можно предоставить другим решениям, включая другие решения Microsoft Office. Это полезно, если надстройка VSTO предоставляет службу, доступ к которой нужно предоставить другим решениям. Например если у вас есть надстройки VSTO для Microsoft Office Excel, которая выполняет вычисление финансовых данных из веб-службы, другие решения могут выполнять эти вычисления, вызывая надстройки VSTO для Excel во время выполнения.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Этот процесс включает два основных этапа.

- В надстройке VSTO предоставьте доступ к объекту другим решениям.

- В другом решении обратитесь к объекту, предоставленному надстройкой VSTO, и вызовите члены объекта.

## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Типы решений, которые можно вызывать код в надстройке
 Можно предоставить объект в надстройке VSTO для следующих типов решений:

- код Visual Basic для приложений (VBA) в документе, который загружается в тот же процесс приложения, что и надстройка VSTO;

- настройки уровня документа, которые загружаются в тот же процесс приложения, что и надстройка VSTO;

- другие надстройки VSTO, созданные с помощью шаблонов проектов Office в Visual Studio;

- надстройки VSTO COM (то есть надстройки VSTO, реализующие интерфейс <xref:Extensibility.IDTExtensibility2> напрямую);

- любые решения, выполняющиеся в процессе, который отличается от процесса надстройки VSTO (эти типы решений также называют *внепроцессными клиентами*). К ним относятся приложения, автоматизирующие работу приложений Office, такие как Windows Forms или консольное приложение, а также надстройки VSTO, загружаемые в другой процесс.

## <a name="expose-objects-to-other-solutions"></a>Представления объектов в другие решения
 Чтобы предоставить доступ к объекту в надстройке VSTO другим решениям, выполните в надстройке VSTO указанные ниже действия.

1. Определите класс, которые требуется предоставлять другим решениям.

2. Переопределите метод <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> в классе `ThisAddIn` . Верните экземпляр класса, который требуется предоставлять другим решениям.

### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>Определите класс, который вы хотите предоставить другим решениям
 Как минимум, предоставляемый класс должен быть общим, для атрибута этого класса <xref:System.Runtime.InteropServices.ComVisibleAttribute> должно быть задано значение **true**и он должен предоставлять интерфейс [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) .

 Предоставление интерфейса [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) рекомендуется выполнять следующим образом.

1. Определите интерфейс, объявляющий члены, которые требуется предоставить другим решениям. Этот интерфейс можно определить в проекте надстройки VSTO. Однако может потребоваться определить его в отдельном проекте библиотеки класса, если класс потребуется предоставлять решениям, не основанным на VBA. Это позволит решениям, вызывающим вашу надстройку VSTO, ссылаться на интерфейс, не ссылаясь на проект надстройки VSTO.

2. Примените атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute> к этому интерфейсу и задайте для него значение **true**.

3. Измените класс для реализации этого интерфейса.

4. Применить <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> к классу атрибут и присвоить этому атрибуту значение **None** значение <xref:System.Runtime.InteropServices.ClassInterfaceType> перечисления.

5. Если вы хотите предоставить этот класс клиентам вне процесса, может также потребоваться сделайте следующее:

   - Создайте класс, производный от <xref:System.Runtime.InteropServices.StandardOleMarshalObject>. Дополнительные сведения см. в разделе [предоставлять классы клиентам вне процесса](#outofproc).

   - Задайте свойство **Регистрация для COM-взаимодействия** в проекте, в которым вы определили интерфейс. Это свойство необходимо, только в том случае, если вы хотите разрешить клиентам использовать раннее связывание для вызова надстройки VSTO.

   Следующие примеры кода демонстрируют класс `AddInUtilities` с методом `ImportData` , который может вызываться другими решениями. Этот код в контексте более крупного пошагового руководства, см. в разделе [Пошаговое руководство: Вызов кода в надстройке VSTO из VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

   [!code-csharp[Trin_AddInInteropWalkthrough #3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
   [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]

### <a name="expose-classes-to-vba"></a>Предоставление классов VBA
 Если вы выполните приведенные выше действия, код VBA сможет вызывать только те методы, которые будут объявлены в интерфейсе. Код VBA не может вызывать остальные методы в классе, включая методы, получаемые классом из базовых классов, таких как <xref:System.Object>.

 Можно также предоставить [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) интерфейса, установив <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибуту значение AutoDispatch или AutoDual <xref:System.Runtime.InteropServices.ClassInterfaceType> перечисления. Если предоставить интерфейс, у вас нет объявлять методы в отдельном интерфейсе. Тем не менее код VBA сможет вызывать все общие и нестатические методы в классе, включая полученные из базовых классов, таких как <xref:System.Object>. Кроме того, внепроцессные клиенты, использующие раннее связывание, не смогут вызывать ваш класс.

### <a name="outofproc"></a> Предоставление классов клиентам вне процесса
 Чтобы предоставить класс в надстройке VSTO внепроцессным клиентам, необходимо создать класс, производный от <xref:System.Runtime.InteropServices.StandardOleMarshalObject> . Это гарантирует, что внепроцессные клиенты смогут вызывать предоставленный объект надстройки VSTO. В противном случае попытки получить экземпляр предоставленного объекта во внепроцессном клиенте может завершиться неожиданным сбоем.

 Этот сбой — так как все вызовы объектной модели приложения Office должны выполняться в основном потоке пользовательского интерфейса, но вызовы от клиента вне процесса вашего объекта будут поступать в произвольном потоке RPC (удаленный вызов процедуры). Механизм маршалинга COM в .NET Framework не переключает потоки и вместо этого попытается выполнить маршалинг вызова в объект для входящего потока RPC вместо основного потока пользовательского интерфейса. Если объект является экземпляром класса, производного от <xref:System.Runtime.InteropServices.StandardOleMarshalObject>, для входящих вызовов вашего объекта автоматически выполняется маршалинг в поток, в котором был создан предоставляемый объект (то есть в основной поток пользовательского интерфейса ведущего приложения).

 Дополнительные сведения об использовании потоков в решениях Office см. в разделе [поддержка потоков в Office](../vsto/threading-support-in-office.md).

### <a name="override-the-requestcomaddinautomationservice-method"></a>Переопределение метода RequestComAddInAutomationService
 Следующий пример кода демонстрирует переопределение метода <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> в классе `ThisAddIn` в надстройке VSTO. В примере предполагается, что вы определили класс с именем `AddInUtilities` , требуется предоставить другим решениям. Этот код в контексте более крупного пошагового руководства, см. в разделе [Пошаговое руководство: Вызов кода в надстройке VSTO из VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]

 При загрузке надстройки VSTO [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает метод <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . Среда выполнения назначает возвращаемый объект свойству COMAddIn.Object <xref:Microsoft.Office.Core.COMAddIn> , представляющий Ваша надстройка VSTO. Этот объект <xref:Microsoft.Office.Core.COMAddIn> доступен для других решений Office, а также для решений, отвечающих за автоматизацию Office.

## <a name="access-objects-from-other-solutions"></a>Доступ к объектам из других решений
 Чтобы вызвать предоставляемый объект в вашей надстройке VSTO, выполните в клиентском решении указанные ниже действия.

1. Получите объект <xref:Microsoft.Office.Core.COMAddIn> , представляющий предоставляемую надстройку VSTO. Клиенты могут получать доступ ко всем доступным надстройкам VSTO, используя свойство `Application.COMAddIns` в объектной модели ведущего приложения Office.

2. Доступ к свойству COMAddIn.Object <xref:Microsoft.Office.Core.COMAddIn> объекта. Это свойство возвращает предоставленный объект из надстройки VSTO.

3. Вызовите члены предоставляемого объекта.

   Способ использовать возвращаемое значение свойства COMAddIn.Object отличается для клиентов VBA и клиентов, не основанных на VBA. Для внепроцессных клиентов требуется дополнительный код, который позволит избежать возникновения состояния гонки.

### <a name="access-objects-from-vba-solutions"></a>Доступ к объектам из решений VBA
 В следующем примере кода демонстрируется использование VBA для вызова метода, который предоставляется надстройкой VSTO. Этот макрос VBA вызывает метод с именем `ImportData` , определенный в надстройке VSTO, которая называется **ExcelImportData**. Этот код в контексте более крупного пошагового руководства, см. в разделе [Пошаговое руководство: Вызов кода в надстройке VSTO из VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

```vb
Sub CallVSTOMethod()
    Dim addIn As COMAddIn
    Dim automationObject As Object
    Set addIn = Application.COMAddIns("ExcelImportData")
    Set automationObject = addIn.Object
    automationObject.ImportData
End Sub
```

### <a name="access-objects-from-non-vba-solutions"></a>Доступ к объектам из решений не основанных на VBA
 В решении не основанных на VBA необходимо привести значение свойства COMAddIn.Object интерфейс, который он реализует, и затем можно вызывать предоставленные методы в объекте интерфейса. В следующем примере кода показано, как вызвать метод `ImportData` из другой надстройки VSTO, которая была создана с помощью набора Office Developer Tools в Visual Studio.

```vb
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _
    addIn.Object, ExcelImportData.IAddInUtilities)
utilities.ImportData()
```

```csharp
object addInName = "ExcelImportData";
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;
utilities.ImportData();
```

 В этом примере при попытке привести значение свойства COMAddIn.Object `AddInUtilities` класса, а не `IAddInUtilities` интерфейс, код создаст исключение <xref:System.InvalidCastException>.

## <a name="see-also"></a>См. также
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Пошаговое руководство: Вызов кода в надстройке VSTO из VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Разработка решений Office](../vsto/developing-office-solutions.md)
- [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Настройка возможностей пользовательского интерфейса с помощью интерфейсов расширяемости](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
