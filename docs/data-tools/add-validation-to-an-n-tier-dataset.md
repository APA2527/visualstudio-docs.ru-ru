---
title: Добавление проверки в n-уровневом наборе данных
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4fdeef3a21407b4473ed412019e936d7b30389c5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402883"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Добавление проверки в n-уровневом наборе данных
Добавление проверки к набору данных в n уровневого решения по сути является таким же, как добавление проверки к набору данных одного файла (набор данных в одном проекте). Предлагаемое местоположение для выполнения проверки данных — во время <xref:System.Data.DataTable.ColumnChanging> и/или <xref:System.Data.DataTable.RowChanging> события таблицы данных.

 Набор данных предоставляет возможность создания разделяемых классов, к которым можно добавить пользовательский код для события изменения столбца и строки таблиц данных в наборе данных. Дополнительные сведения о добавлении кода в набор данных в n уровневого решения, см. в разделе [Добавление кода для наборов данных в n уровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md), и [добавьте код для объектов TableAdapter в многоуровневых приложениях](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Дополнительные сведения о разделяемых классах см. в разделе [как: Разделение класса на разделяемые классы (конструктор классов)](../ide/class-designer/how-to-split-a-class-into-partial-classes.md) или [разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

> [!NOTE]
> При разделении наборов данных из адаптеров таблиц (задавая **проект DataSet** свойство), существующие разделяемые классы наборов данных в проекте не перемещаются автоматически. Существующие разделяемые классы наборов данных должны быть вручную перемещены в проект набора данных.

> [!NOTE]
> Конструктор набора данных не создает автоматически обработчики событий в C# для <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging> события. Вам нужно вручную создать обработчик событий и подключить обработчик событий, соответствующем событии. Следующие процедуры описывают создание обработчиков событий в Visual Basic и C#.

## <a name="validate-changes-to-individual-columns"></a>Проверить изменения в отдельных столбцах
 Проверка значений в отдельных столбцах при обработке <xref:System.Data.DataTable.ColumnChanging> событий. <xref:System.Data.DataTable.ColumnChanging> Событие возникает при изменении значения в столбце. Создайте обработчик событий для <xref:System.Data.DataTable.ColumnChanging> событий, дважды щелкнув требуемый столбец **конструктор наборов данных**.

 Первый раз, дважды щелкните столбец, конструктор создает обработчик событий для <xref:System.Data.DataTable.ColumnChanging> событий. `If...Then` Также создается инструкция, тесты для определенного столбца. Например, следующий код формируется при двойном щелчке **RequiredDate** столбец таблицы Northwind Orders:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> В проектах C# конструктор наборов данных создает только разделяемые классы для набора данных и отдельные таблицы в наборе данных. Конструктор наборов данных не создает автоматически обработчики событий для <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging> событий в C#, как и в Visual Basic. В проектах C# необходимо вручную создать метод для обработки события и подключить метод базового события. Ниже описывается, как создавать обработчики событий в Visual Basic и C#.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Чтобы добавить проверку во время изменения к отдельным значениям в столбце

1. Откройте набор данных, дважды щелкнув *.xsd* файл **обозревателе решений**. Дополнительные сведения см. в разделе [Пошаговое руководство: Создание набора данных в конструкторе наборов данных](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Дважды щелкните столбец, который требуется проверить. Это действие создает <xref:System.Data.DataTable.ColumnChanging> обработчик событий.

    > [!NOTE]
    > Конструктор наборов данных не создает автоматически обработчик событий для события C#. Код, который необходимо обработать событие в C# входит в следующем разделе. `SampleColumnChangingEvent` создается и затем подключается к <xref:System.Data.DataTable.ColumnChanging> событие в <xref:System.Data.DataTable.EndInit%2A> метод.

3. Добавьте код, чтобы убедиться, что `e.ProposedValue` содержит данные, которые удовлетворяют требованиям приложения. Если предложенное значение является недопустимым, задайте столбец для указания, что он содержит ошибку.

     В следующем примере кода проверяет, что **количество** столбец содержит значение больше 0. Если **количество** меньше или равно 0, столбцу присваивается ошибку. `Else` Предложение ошибка устраняется, если **количество** больше, чем 0. Код в обработчик событий изменения столбца должен выглядеть следующим образом:

    ```vb
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then
        If CType(e.ProposedValue, Short) <= 0 Then
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")
        Else
            e.Row.SetColumnError(e.Column, "")
        End If
    End If
    ```

    ```csharp
    // Add this code to the DataTable partial class.

    public override void EndInit()
    {
        base.EndInit();
        // Hook up the ColumnChanging event
        // to call the SampleColumnChangingEvent method.
        ColumnChanging += SampleColumnChangingEvent;
    }

    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)
    {
        if (e.Column.ColumnName == QuantityColumn.ColumnName)
        {
            if ((short)e.ProposedValue <= 0)
            {
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
            }
            else
            {
                e.Row.SetColumnError("Quantity", "");
            }
        }
    }
    ```

## <a name="validate-changes-to-whole-rows"></a>Проверка изменения всей строки
 Проверка значений во всей строке при обработке <xref:System.Data.DataTable.RowChanging> событий. <xref:System.Data.DataTable.RowChanging> Событие возникает, когда значения во всех столбцах будут зафиксированы. Это необходимо для проверки в <xref:System.Data.DataTable.RowChanging> событие, когда значение в один столбец основывается на значении в другом столбце. Например рассмотрим OrderDate и RequiredDate в таблице Orders в Northwind.

 После ввода заказов проверки гарантирует, что заказ не введен с RequiredDate, который во время или до OrderDate. В этом примере значения для столбцов OrderDate и RequiredDate необходимо сравнить, поэтому проверка изменения отдельных столбцов не имеет смысла.

 Создайте обработчик событий для <xref:System.Data.DataTable.RowChanging> событий, дважды щелкнув имя таблицы в строке заголовка таблицы **конструктор наборов данных**.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Чтобы добавить проверку во время изменения для всех строк

1. Откройте набор данных, дважды щелкнув *.xsd* файл **обозревателе решений**. Дополнительные сведения см. в разделе [Пошаговое руководство: Создание набора данных в конструкторе наборов данных](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Дважды щелкните заголовок таблицы данных в конструкторе.

     Разделяемый класс создается с `RowChanging` обработчик событий и откроется в редакторе кода.

    > [!NOTE]
    > Конструктор наборов данных не создает автоматически обработчик событий для <xref:System.Data.DataTable.RowChanging> событий в проектах C#. Необходимо создать метод для обработки <xref:System.Data.DataTable.RowChanging> событий и выполнения кода, которые затем подключить событие в методе инициализации таблицы.

3. Добавьте код внутри объявления частичного класса.

4. В следующем коде показано, где можно добавить пользовательский код для проверки во время <xref:System.Data.DataTable.RowChanging> событий. В примере C# также включает в себя код для подключения до метода обработчика событий `OrdersRowChanging` событий.

    ```vb
    Partial Class OrdersDataTable
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging
            ' Add logic to validate columns here.
            If e.Row.RequiredDate <= e.Row.OrderDate Then
                ' Set the RowError if validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"
            Else
                ' Clear the RowError when validation passes.
                e.Row.RowError = ""
            End If
        End Sub
    End Class
    ```

    ```csharp
    partial class OrdersDataTable
    {
        public override void EndInit()
        {
            base.EndInit();
            // Hook up the event to the
            // RowChangingEvent method.
            OrdersRowChanging += RowChangingEvent;
        }

        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)
        {
            // Perform the validation logic.
            if (e.Row.RequiredDate <= e.Row.OrderDate)
            {
                // Set the row to an error when validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";
            }
            else
            {
                // Clear the RowError if validation passes.
                e.Row.RowError = "";
            }
        }
    }
    ```

## <a name="see-also"></a>См. также

- [Общие сведения об n-уровневых приложениях](../data-tools/n-tier-data-applications-overview.md)
- [Пошаговое руководство: Создание N-уровневого приложения для работы с данными](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Проверка данных в наборах данных](../data-tools/validate-data-in-datasets.md)