---
title: Заполнение наборов данных с помощью адаптеров таблицы
description: Заполнение наборов данных с помощью адаптеров таблиц TableAdapter. Компонент TableAdapter заполняет набор данных данными из БД на основе одного или нескольких указанных запросов или хранимых процедур.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 8037b8d19bad19485e9ed8f7926e6a3e45b8fef1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866909"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Заполнение наборов данных с помощью адаптеров таблицы

Компонент TableAdapter заполняет набор данных данными из базы данных на основе одного или нескольких указанных запросов или хранимых процедур. TableAdapter также может выполнять операции добавления, обновления и удаления в базе данных для сохранения изменений, внесенных в набор данных. Кроме того, можно выдавать глобальные команды, не связанные ни с одной конкретной таблицей.

> [!NOTE]
> Адаптеры таблиц создаются конструкторами Visual Studio. Если наборы данных создаются программно, используйте DataAdapter, который является классом .NET.

Подробные сведения об операциях TableAdapter можно пропустить непосредственно в одном из следующих разделов:

|Раздел|Описание|
|-----------|-----------------|
|[Создание и настройка адаптеров таблиц TableAdapter](../data-tools/create-and-configure-tableadapters.md)|Использование конструкторов для создания и настройки адаптеров таблиц|
|[Создание параметризованных запросов адаптера таблицы TableAdapter](../data-tools/create-parameterized-tableadapter-queries.md)|Как разрешить пользователям предоставлять аргументы для процедур или запросов TableAdapter|
|[Непосредственный доступ к базе данных с помощью адаптера таблицы TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Использование методов DBDirect для адаптеров таблиц TableAdapter|
|[Отключение ограничений при заполнении набора данных](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Работа с ограничениями внешнего ключа при обновлении данных|
|[Практическое руководство. Расширение функциональных возможностей адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)|Добавление пользовательского кода в TableAdapter|
|[Считывание XML-данных в набор данных](../data-tools/read-xml-data-into-a-dataset.md)|Работа с XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>Общие сведения об адаптере таблиц

Адаптеры таблиц — это компоненты, создаваемые конструктором, которые подключаются к базе данных, выполняют запросы или хранимые процедуры и заполняют их таблицу данных возвращаемыми данными. Адаптеры таблиц также отправляют обновленные данные из приложения обратно в базу данных. В TableAdapter можно выполнять столько запросов, сколько нужно, если они возвращают данные, соответствующие схеме таблицы, с которой связан TableAdapter. На следующей схеме показано взаимодействие адаптеров таблиц с базами данных и другими объектами в памяти.

![Поток данных в клиентском приложении](../data-tools/media/clientdatadiagram.gif)

Хотя адаптеры таблиц разработаны с **Конструктор наборов данных**, классы TableAdapter не создаются как вложенные классы  <xref:System.Data.DataSet> . Они находятся в отдельных пространствах имен, относящихся к каждому набору данных. Например, если имеется набор данных с именем `NorthwindDataSet` , адаптеры таблиц TableAdapter, связанные с  <xref:System.Data.DataTable> s в, `NorthwindDataSet` будут находиться в `NorthwindDataSetTableAdapters` пространстве имен. Чтобы получить доступ к определенному адаптеру TableAdapter программным путем, необходимо объявить новый экземпляр TableAdapter. Пример:

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Связанная схема DataTable

При создании TableAdapter используется первоначальный запрос или хранимая процедура для определения схемы, связанной с TableAdapter <xref:System.Data.DataTable> . Этот начальный запрос или хранимая процедура запускается путем вызова `Fill` метода TableAdapter (который заполняет связанный адаптер таблицы <xref:System.Data.DataTable> ). Любые изменения, внесенные в основной запрос TableAdapter, отражаются в схеме связанной таблицы данных. Например, при удалении столбца из основного запроса также удаляется столбец из связанной таблицы данных. Если любые дополнительные запросы к TableAdapter используют инструкции SQL, возвращающие столбцы, которые не находятся в основном запросе, конструктор пытается синхронизировать изменения столбцов между основным запросом и дополнительными запросами.

## <a name="tableadapter-update-commands"></a>Команды обновления TableAdapter

Функции обновления TableAdapter зависят от того, какой объем информации доступен в основном запросе в **мастере TableAdapter**. Например, адаптеры таблиц, настроенные для выборки значений из нескольких таблиц (с помощью `JOIN` ), скалярных значений, представлений или результатов агрегатных функций, изначально не создаются с возможностью отправки обновлений в основную базу данных. Однако `INSERT` команды, и можно настроить `UPDATE` `DELETE` вручную в окне **Свойства** .

## <a name="tableadapter-queries"></a>запросы TableAdapter

![TableAdapter с несколькими запросами](../data-tools/media/tableadapter.gif)

Адаптеры таблиц могут содержать несколько запросов для заполнения связанных таблиц данных. Можно определить столько запросов для TableAdapter, сколько требуется приложению, при условии, что каждый запрос возвращает данные, соответствующие той же схеме, что и связанная с ней таблица данных. Эта возможность позволяет адаптеру таблицы загружать различные результаты на основе различных критериев.

Например, если приложение содержит таблицу с именами клиентов, можно создать запрос, который заполняет таблицу всеми именами клиентов, начинающимися с определенной буквы, а другая заполняет таблицу всеми клиентами, находящимися в том же состоянии. Чтобы заполнить `Customers` таблицу клиентами в заданном состоянии, можно создать `FillByState` запрос, который принимает параметр для значения State следующим образом: `SELECT * FROM Customers WHERE State = @State` . Запрос выполняется путем вызова `FillByState` метода и передачи значения параметра следующим образом: `CustomerTableAdapter.FillByState("WA")` .

Помимо добавления запросов, возвращающих данные той же схемы, что и таблица данных TableAdapter, можно добавлять запросы, возвращающие скалярные (одиночные) значения. Например, запрос, возвращающий число клиентов (), `SELECT Count(*) From Customers` допустим для, `CustomersTableAdapter,` даже если возвращаемые данные не соответствуют схеме таблицы.

## <a name="clearbeforefill-property"></a>Клеарбефорефилл, свойство

По умолчанию при каждом выполнении запроса на заполнение таблицы данных TableAdapter существующие данные очищаются, а в таблицу загружаются только результаты запроса. Задайте `ClearBeforeFill` для свойства TableAdapter значение `false` , если требуется добавить или объединить данные, возвращаемые запросом, с существующими данными в таблице данных. Независимо от того, очищены ли данные, необходимо явно отправить обновления обратно в базу данных, если нужно их сохранить. Поэтому не забывайте сохранять изменения в данных в таблице перед выполнением другого запроса, который заполняет таблицу. Дополнительные сведения см. [в разделе Обновление данных с помощью TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Наследование TableAdapter

TableAdapter расширяют функциональные возможности стандартных адаптеров данных путем инкапсуляции настроенного <xref:System.Data.Common.DataAdapter> класса. По умолчанию TableAdapter наследует от <xref:System.ComponentModel.Component> класса и не может быть приведен к <xref:System.Data.Common.DataAdapter> классу. Приведение TableAdapter к <xref:System.Data.Common.DataAdapter> классу приводит к <xref:System.InvalidCastException> ошибке. Чтобы изменить базовый класс TableAdapter, можно указать класс, производный от, <xref:System.ComponentModel.Component> в свойстве **базового класса** TableAdapter в **Конструктор наборов данных**.

## <a name="tableadapter-methods-and-properties"></a>Методы и свойства TableAdapter

Класс TableAdapter не является типом .NET. Это означает, что вы не можете найти его в документации или в **обозревателе объектов**. Он создается во время разработки при использовании одного из мастеров, упомянутых ранее. Имя, назначенное TableAdapter при его создании, основано на имени таблицы, с которой вы работаете. Например, при создании TableAdapter, основанного на таблице в базе данных с именем `Orders` , TableAdapter будет называться `OrdersTableAdapter` . Имя класса TableAdapter можно изменить с помощью свойства **Name** в **Конструктор наборов данных**.

Ниже перечислены часто используемые методы и свойства адаптеров таблиц.

|Член|Описание|
|------------|-----------------|
|`TableAdapter.Fill`|Заполняет таблицу связанных данных TableAdapter результатами выполнения `SELECT` команды TableAdapter.|
|`TableAdapter.Update`|Отправляет изменения обратно в базу данных и возвращает целое число, представляющее количество строк, затронутых обновлением. Дополнительные сведения см. [в разделе Обновление данных с помощью TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Возвращает новый объект <xref:System.Data.DataTable> , заполненный данными.|
|`TableAdapter.Insert`|Создает новую строку в таблице данных. Дополнительные сведения см. [в разделе Вставка новых записей в базу данных](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Определяет, очищается ли таблица данных перед вызовом одного из `Fill` методов.|

## <a name="tableadapter-update-method"></a>Метод обновления адаптера таблицы

Адаптеры таблиц используют команды данных для чтения и записи из базы данных. Используйте первоначальный `Fill` (основной) запрос TableAdapter в качестве основания для создания схемы связанной таблицы данных, а также `InsertCommand` `UpdateCommand` команд, и, `DeleteCommand` связанных с `TableAdapter.Update` методом. При вызове `Update` метода TableAdapter выполняются инструкции, созданные при первоначальной настройке TableAdapter, а не один из дополнительных запросов, добавленных с помощью **мастера настройки запросов TableAdapter**.

При использовании TableAdapter он фактически выполняет те же операции с командами, которые обычно выполняются. Например, при вызове `Fill` метода адаптера адаптер выполняет команду данных в своем `SelectCommand` свойстве и использует модуль чтения данных (например, <xref:System.Data.SqlClient.SqlDataReader> ) для загрузки результирующего набора в таблицу данных. Аналогично, при вызове метода адаптера `Update` он выполняет соответствующую команду (в `UpdateCommand` `InsertCommand` `DeleteCommand` свойствах, и) для каждой измененной записи в таблице данных.

> [!NOTE]
> Если в основном запросе достаточно сведений, `InsertCommand` `UpdateCommand` команды, и `DeleteCommand` создаются по умолчанию при создании адаптера таблицы. Если основной запрос TableAdapter является более чем одной `SELECT` инструкцией Table, конструктор не сможет создавать `InsertCommand` , `UpdateCommand` и `DeleteCommand` . Если эти команды не создаются, при выполнении метода может появиться сообщение об ошибке `TableAdapter.Update` .

## <a name="tableadapter-generatedbdirectmethods"></a>GenerateDbDirectMethods адаптера таблицы

Помимо `InsertCommand` , `UpdateCommand` и `DeleteCommand` , адаптеры таблиц создаются с помощью методов, которые можно запускать непосредственно в базе данных. Эти методы ( `TableAdapter.Insert` , `TableAdapter.Update` и) можно вызывать `TableAdapter.Delete` непосредственно для работы с данными в базе данных. Это означает, что вы можете вызывать эти отдельные методы из кода вместо вызова `TableAdapter.Update` для обработки операций вставки, обновления и удаления, ожидающих связанной таблицы данных.

Если вы не хотите создавать эти прямые методы, задайте для свойства **GenerateDBDirectMethods** TableAdapter значение `false` (в окне " **Свойства** "). Дополнительные запросы, добавляемые в TableAdapter, являются автономными запросами — они не создают эти методы.

## <a name="tableadapter-support-for-nullable-types"></a>Поддержка TableAdapter для типов, допускающих значение null

Адаптеры таблиц поддерживают типы, допускающие значение NULL `Nullable(Of T)` , и `T?` . Дополнительные сведения о типах, допускающих значение NULL, в Visual Basic см. в разделе [Типы значений, допускающие значение NULL](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Дополнительные сведения о типах Nullable в C# см. в разделе [Использование типов, допускающих значение NULL](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>Справочник по TableAdapterManager

По умолчанию класс TableAdapterManager создается при создании набора данных, содержащего связанные таблицы. Чтобы предотвратить создание класса, измените значение `Hierarchical Update` Свойства набора данных на false. При перетаскивании таблицы, имеющей отношение, в область конструктора на странице Windows Form или WPF, Visual Studio объявляет переменную-член класса. Если не используется привязка данных, необходимо вручную объявить переменную.

Класс TableAdapterManager не является типом .NET. Поэтому вы не можете найти его в документации. Он создается во время разработки в рамках процесса создания набора данных.

Ниже приведены часто используемые методы и свойства `TableAdapterManager` класса.

|Член|Описание|
|------------|-----------------|
|Метод `UpdateAll`|Сохраняет все данные из всех таблиц данных.|
|Свойство`BackUpDataSetBeforeUpdate`|Определяет, следует ли создать резервную копию набора данных перед выполнением `TableAdapterManager.UpdateAll` метода. Логическая.|
|*TableName* `TableAdapter` свойства|Представляет адаптер таблицы. Созданный TableAdapterManager содержит свойство для каждого элемента `TableAdapter` управления. Например, набор данных с таблицей Customers и Orders создается с помощью TableAdapterManager, который содержит `CustomersTableAdapter` `OrdersTableAdapter` Свойства и.|
|Свойство`UpdateOrder`|Управляет порядком отдельных команд вставки, обновления и удаления. Задайте для этого параметра одно из значений `TableAdapterManager.UpdateOrderOption` перечисления.<br /><br /> По умолчанию для задано `UpdateOrder` значение **инсертупдатеделете**. Это означает, что операции вставки, обновления и удаления выполняются для всех таблиц в наборе данных.|

## <a name="security"></a>Безопасность

При использовании команд данных со свойством CommandType, имеющим значение <xref:System.Data.CommandType.Text> , внимательно проверяйте сведения, отправляемые с клиента, перед их передачей в базу данных. Злоумышленники могут попытаться отправить (внедрить) модифицированные или добавочные инструкции SQL и получить незаконный доступ к базе данных или повредить ее. Прежде чем передавать данные, введенные пользователем, в базу данных, всегда проверяйте, являются ли сведения допустимыми. Рекомендуется всегда использовать параметризованные запросы или хранимые процедуры, если это возможно.

## <a name="see-also"></a>См. также раздел

- [Инструменты набора данных](../data-tools/dataset-tools-in-visual-studio.md)
