---
title: 记录字段交换：RFX 的工作方式
ms.date: 11/04/2016
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
ms.openlocfilehash: 9e717d0f0ce3b8841feee2beb457fee7221fcf69
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403785"
---
# <a name="record-field-exchange-how-rfx-works"></a>记录字段交换：RFX 的工作方式

本主题介绍 RFX 过程。 这是一个高级主题，涵盖：

- [RFX 和记录集](#_core_rfx_and_the_recordset)

- [RFX 过程](#_core_the_record_field_exchange_process)

> [!NOTE]
> 本主题适用于从 `CRecordset` 派生的类，其中尚未实现批量提取行。 如果使用批量提取行，则将实现批量记录字段交换（批量 RFX）。 批量 RFX 与 RFX 类似。 若要了解不同之处，请参阅[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

## <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a>RFX 和记录集

收集的记录集对象的字段数据成员组成一个编辑缓冲区，其中包含一条记录的选定列。 当第一次打开记录集并将要读取第一条记录时，RFX 将每个所选列绑定到相应字段数据成员的地址。 当记录集更新记录时，RFX 调用 ODBC API 函数向驱动程序发送 SQL **UPDATE**或**INSERT**语句。 RFX 使用其字段数据成员的知识来指定要写入的列。

框架在某些阶段备份编辑缓冲区，以便它可以在必要时还原其内容。 RFX 在添加新记录之前和编辑现有记录之前备份编辑缓冲区。 在某些情况下（例如，在调用之后），它将还原编辑缓冲区 `Update` `AddNew` 。 如果在调用前放弃新的编辑缓冲区（例如，将其移至另一个记录），则不会还原编辑缓冲区 `Update` 。

除了在数据源和记录集的字段数据成员之间交换数据以外，RFX 还管理绑定参数。 当打开该记录集时，所有参数数据成员都按构造的 SQL 语句中的 "？" 占位符的顺序进行绑定 `CRecordset::Open` 。 有关详细信息，请参阅[记录集：参数化记录集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

记录集类的重写 `DoFieldExchange` 执行所有工作，并在双向移动数据。 与对话框数据交换（DDX）一样，RFX 需要有关类的数据成员的信息。 向导通过为您编写记录集特定的实现来提供必要的信息 `DoFieldExchange` ，具体取决于您在向导中指定的字段数据成员名称和数据类型。

## <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a>记录字段交换过程

本部分介绍了在您添加、更新和删除记录时作为记录集对象打开和记录的 RFX 事件的顺序。 [记录集期间 Rfx 操作](#_core_sequence_of_rfx_operations_during_recordset_open)的表序列和[滚动过程中 rfx 操作](#_core_sequence_of_rfx_operations_during_scrolling)的表序列会在 rfx 处理记录集中的命令时显示此过程 `Move` ，而 rfx 管理更新。 在这些过程中，将调用[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)来执行多种不同的操作。 `m_nOperation` [CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象的数据成员确定请求的操作。 您可能会发现读取记录集很有帮助：记录集[如何选择记录（odbc）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)和[记录集：记录集如何更新记录（ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) 。

### <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX：列和参数的初始绑定

调用记录集对象的[Open](../../mfc/reference/crecordset-class.md#open)成员函数时，将按显示的顺序发生以下 RFX 活动：

- 如果记录集具有参数数据成员，则框架将调用 `DoFieldExchange` 以将参数绑定到记录集的 SQL 语句字符串中的参数占位符。 参数值的数据类型依赖表示形式用于在**SELECT**语句中找到的每个占位符。 在 SQL 语句准备好之后但在执行之前，会发生这种情况。 有关语句准备的信息，请参阅 `::SQLPrepare` ODBC*程序员参考*中的函数。

- 框架再次调用 `DoFieldExchange` 以将所选列的值绑定到记录集中的相应字段数据成员。 这会将 recordset 对象建立为包含第一条记录的列的编辑缓冲区。

- 记录集执行 SQL 语句，数据源选择第一条记录。 记录的列将加载到记录集的字段数据成员中。

下表显示了打开记录集时 RFX 操作的顺序。

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>记录集打开过程中 RFX 操作的顺序

|你的操作|DoFieldExchange 操作|数据库/SQL 操作|
|--------------------|-------------------------------|-----------------------------|
|1. 打开记录集。|||
||2. 生成 SQL 语句。||
|||3. 发送 SQL。|
||4. 绑定参数数据成员。||
||5. 将字段数据成员绑定到列。||
|||6. ODBC 执行移动并填充数据。|
||7. 修复 c + + 数据。||

记录集使用 ODBC 的准备好的执行，以允许使用相同的 SQL 语句进行快速的重新查询。 有关已准备执行的详细信息，请参阅[ODBC 程序员参考](/sql/odbc/reference/odbc-programmer-s-reference)。

### <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a>RFX：滚动

从一条记录滚动到另一条记录时，框架会调用 `DoFieldExchange` 将以前存储在字段数据成员中的值替换为新记录的值。

下表显示用户从记录移到记录时 RFX 操作的顺序。

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a>滚动过程中 RFX 操作的顺序

|你的操作|DoFieldExchange 操作|数据库/SQL 操作|
|--------------------|-------------------------------|-----------------------------|
|1. 调用 `MoveNext` 或其他移动函数之一。|||
|||2. 若要移动和填充数据，ODBC 会执行此项。|
||3. 修复 c + + 数据。||

### <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX：添加新记录和编辑现有记录

如果添加新记录，记录集将作为编辑缓冲区运行，以生成新记录的内容。 与添加记录一样，编辑记录包括更改记录集的字段数据成员的值。 从 RFX 的角度来看，顺序如下：

1. 对记录集的[AddNew](../../mfc/reference/crecordset-class.md#addnew)或[Edit](../../mfc/reference/crecordset-class.md#edit)成员函数的调用会导致 RFX 存储当前编辑缓冲区，以便以后可以还原。

1. `AddNew`或 `Edit` 准备编辑缓冲区中的字段，以便 RFX 可以检测已更改的字段数据成员。

   由于新记录没有先前值用于比较新记录，因此 `AddNew` 将每个字段数据成员的值设置为 PSEUDO_NULL 值。 以后调用时 `Update` ，RFX 会将每个数据成员的值与 PSEUDO_NULL 值进行比较。 如果存在差异，则已设置数据成员。 （PSEUDO_NULL 与具有 true Null 值的记录列不同，也不是与 c + + NULL 相同。）

   与对的 `Update` 调用不同 `AddNew` ， `Update` 对的调用会将 `Edit` 更新的值与以前存储的值进行比较，而不是使用 PSEUDO_NULL。 差别在于， `AddNew` 没有以前存储的值进行比较。

1. 您可以直接设置要编辑其值的字段数据成员的值，也可以直接设置要为新记录填充的值。 这可能包括调用 `SetFieldNull` 。

1. 对已更改的字段数据成员进行[更新](../../mfc/reference/crecordset-class.md#update)检查的调用（请参阅[滚动期间 RFX 操作](#_core_sequence_of_rfx_operations_during_scrolling)的表序列）。 如果没有更改，则 `Update` 返回0。 如果某些字段数据成员已更改，请 `Update` 准备并执行 SQL **INSERT**语句，该语句包含记录中所有已更新字段的值。

1. 对于 `AddNew` ， `Update` 通过还原调用之前的当前记录的以前存储的值来结束 `AddNew` 。 对于 `Edit` ，新的、经过编辑的值仍保持不变。

下表显示了在添加新记录或编辑现有记录时 RFX 操作的顺序。

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>AddNew 和 Edit 期间 RFX 操作的顺序

|你的操作|DoFieldExchange 操作|数据库/SQL 操作|
|--------------------|-------------------------------|-----------------------------|
|1. 调用 `AddNew` 或 `Edit` 。|||
||2. 备份编辑缓冲区。||
||3. 对于 `AddNew` ，将字段数据成员标记为 "清理" 和 Null。||
|4. 向记录集字段数据成员赋值。|||
|5. 调用 `Update` 。|||
||6. 检查已更改的字段。||
||7. 为生成 SQL **INSERT**语句 `AddNew` 或**更新**的语句 `Edit` 。||
|||8. 发送 SQL。|
||9. 对于 `AddNew` ，请将编辑缓冲区还原到其备份的内容。 对于 `Edit` ，删除备份。||

### <a name="rfx-deleting-existing-records"></a>RFX：删除现有记录

删除记录时，RFX 会将所有字段设置为 NULL，提醒您记录已删除，您必须将其移出。 不需要任何其他 RFX 序列信息。

## <a name="see-also"></a>另请参阅

[记录字段交换（RFX）](../../data/odbc/record-field-exchange-rfx.md)<br/>
[MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[宏、全局函数和全局变量](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange 类](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset：:D oFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
