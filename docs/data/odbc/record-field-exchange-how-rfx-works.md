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
ms.openlocfilehash: 903acf4f55fb2708f4998a2babf3f143c895429b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367172"
---
# <a name="record-field-exchange-how-rfx-works"></a>记录字段交换：RFX 的工作方式

本主题介绍 RFX 流程。 这是一个高级主题，涵盖：

- [RFX 和记录集](#_core_rfx_and_the_recordset)

- [RFX 流程](#_core_the_record_field_exchange_process)

> [!NOTE]
> 本主题适用于从 `CRecordset` 派生的类，其中尚未实现批量提取行。 如果使用批量提取行，则将实现批量记录字段交换（批量 RFX）。 批量 RFX 与 RFX 类似。 要了解差异，请参阅[记录集：批量提取记录 （ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a>RFX 和记录集

记录集对象的字段数据成员（一起）构成一个编辑缓冲区，该缓冲区保存一条记录的选定列。 当记录集首次打开并即将读取第一条记录时，RFX 会将每个选定的列绑定（关联）到相应字段数据成员的地址。 当记录集更新记录时，RFX 调用 ODBC API 函数向驱动程序发送 SQL**更新**或**INSERT**语句。 RFX 使用对字段数据成员的知识来指定要写入的列。

框架在某些阶段备份编辑缓冲区，以便在必要时还原其内容。 RFX 在添加新记录之前和编辑现有记录之前备份编辑缓冲区。 在某些情况下，它还原编辑缓冲区，例如，在以下`Update``AddNew`调用之后。 如果放弃新更改的编辑缓冲区，例如，在调用`Update`之前移动到另一条记录，则不会还原编辑缓冲区。

除了在数据源和记录集的字段数据成员之间交换数据外，RFX 还管理绑定参数。 打开记录集时，任何参数数据成员都按`CRecordset::Open`构造的 SQL 语句中的"？ 有关详细信息，请参阅[记录集：参数化记录集 （ODBC）。](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

记录集类的重写`DoFieldExchange`执行所有工作，将数据双向移动。 与对话框数据交换 （DDX） 一样，RFX 需要有关类数据成员的信息。 该向导通过根据向导指定的字段数据成员名称和数据类型为您编写特定于`DoFieldExchange`记录集的实现来提供必要的信息。

## <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a>记录字段交换流程

本节将 RFX 事件的顺序描述为记录集对象被打开以及添加、更新和删除记录时。 本主题中的[RFX 操作在记录集打开期间](#_core_sequence_of_rfx_operations_during_recordset_open)的顺序表[序列和滚动期间 RFX 操作的表序列](#_core_sequence_of_rfx_operations_during_scrolling)显示该过程，因为`Move`RFX 在记录集中处理命令，并且 RFX 管理更新。 在这些过程中[，DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)被调用以执行许多不同的操作。 `m_nOperation` [CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象的数据成员确定请求的操作。 在阅读此材料之前，您可能会发现阅读["记录集：记录集如何选择记录 （ODBC）"](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)和["记录集：记录集如何更新记录"（ODBC）非常有用](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

### <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX：列和参数的初始绑定

调用记录集对象的[Open](../../mfc/reference/crecordset-class.md#open)成员函数时，按照显示的顺序发生以下 RFX 活动：

- 如果记录集具有参数数据成员，则框架将调用`DoFieldExchange`以将参数绑定到记录集 SQL 语句字符串中的参数占位符。 参数值的值的数据类型相关表示形式用于**SELECT**语句中找到的每个占位符。 这将在 SQL 语句准备后，但在执行之前发生。 有关语句准备的信息，请参阅 ODBC`::SQLPrepare`*程序员参考 中的*函数。

- 框架第二`DoFieldExchange`次调用以将所选列的值绑定到记录集中的相应字段数据成员。 这将记录集对象设置为包含第一个记录列的编辑缓冲区。

- 记录集执行 SQL 语句，数据源选择第一条记录。 记录的列将加载到记录集的字段数据成员中。

下表显示了打开记录集时的 RFX 操作顺序。

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>记录集打开期间的 RFX 操作顺序

|你的操作|多菲尔德交换操作|数据库/SQL 操作|
|--------------------|-------------------------------|-----------------------------|
|1. 打开记录集。|||
||2. 构建 SQL 语句。||
|||3. 发送 SQL。|
||4. 绑定参数数据成员。||
||5. 将字段数据成员绑定到列。||
|||6. ODBC 执行移动并填写数据。|
||7. 修复C++的数据。||

记录集使用 ODBC 的已准备执行，以便使用相同的 SQL 语句快速重新查询。 有关准备执行的详细信息，请参阅 MSDN 库中的 ODBC SDK*程序员参考*。

### <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a>RFX：滚动

当您从一条记录滚动到另一个记录时，`DoFieldExchange`框架将调用以新记录的值替换以前存储在字段数据成员中的值。

下表显示了用户从记录移动到记录时的 RFX 操作顺序。

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a>滚动期间的 RFX 操作顺序

|你的操作|多菲尔德交换操作|数据库/SQL 操作|
|--------------------|-------------------------------|-----------------------------|
|1.`MoveNext`呼叫或其他移动功能之一。|||
|||2. ODBC 执行移动并填写数据。|
||3. 修复C++的数据。||

### <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX：添加新记录并编辑现有记录

如果添加新记录，记录集将充当编辑缓冲区以构建新记录的内容。 与添加记录一样，编辑记录涉及更改记录集的字段数据成员的值。 从 RFX 的角度来看，顺序如下：

1. 对记录集的["AddNew"](../../mfc/reference/crecordset-class.md#addnew)或["编辑"](../../mfc/reference/crecordset-class.md#edit)成员函数的调用会导致 RFX 存储当前编辑缓冲区，以便以后可以还原该缓冲区。

1. `AddNew`或`Edit`准备编辑缓冲区中的字段，以便 RFX 可以检测更改的字段数据成员。

   由于新记录没有要比较新值的值，因此`AddNew`将每个字段数据成员的值设置为PSEUDO_NULL值。 稍后，当您调用`Update`时，RFX 将每个数据成员的值与PSEUDO_NULL值进行比较。 如果存在差异，则已设置数据成员。 （PSEUDO_NULL与具有真实 Null 值的记录列不同，或者与 C++ NULL 相同。

   与`Update`的`AddNew`调用不同，`Update`调用`Edit`将更新的值与以前存储的值进行比较，而不是使用PSEUDO_NULL。 区别在于，`AddNew`没有以前存储的值进行比较。

1. 您可以直接设置字段数据成员的值，这些成员的值要编辑或要填充的新记录。 这可以包括调用`SetFieldNull`。

1. 如步骤 2 中所述，对[更新](../../mfc/reference/crecordset-class.md#update)的调用将检查已更改的字段数据成员（请参阅[滚动期间 RFX 操作的表序列](#_core_sequence_of_rfx_operations_during_scrolling)）。 如果没有更改，`Update`则返回 0。 如果某些字段数据成员已更改，`Update`请准备并执行包含记录中所有更新字段的值的 SQL **INSERT**语句。

1. 最后`AddNew`还原`Update``AddNew`调用之前当前记录的以前存储的值。 对于`Edit`，编辑的新值将保留在位。

下表显示了添加新记录或编辑现有记录时 RFX 操作的顺序。

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>添加和编辑期间的 RFX 操作顺序

|你的操作|多菲尔德交换操作|数据库/SQL 操作|
|--------------------|-------------------------------|-----------------------------|
|1.`AddNew`呼叫`Edit`或 。|||
||2. 备份编辑缓冲区。||
||3.`AddNew`对于 ，将字段数据成员标记为"干净"和"空"。||
|4. 将值分配给记录集字段数据成员。|||
|5.`Update`致电 .|||
||6. 检查更改的字段。||
||7. 为**INSERT**`AddNew`生成 SQL INSERT**语句或**更新语句`Edit`。||
|||8. 发送 SQL。|
||9.`AddNew`对于 ，将编辑缓冲区还原到其备份的内容。 对于`Edit`，请删除备份。||

### <a name="rfx-deleting-existing-records"></a>RFX：删除现有记录

删除记录时，RFX 将所有字段设置为 NULL，以提醒该记录已被删除，您必须将其移掉。 您不需要任何其他 RFX 序列信息。

## <a name="see-also"></a>另请参阅

[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[宏、全局函数和全局变量](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange 课程](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset：:DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
