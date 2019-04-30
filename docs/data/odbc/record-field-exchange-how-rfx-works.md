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
ms.openlocfilehash: 7da9d480f16dcb6bc5ded0a1dff559b1b1ac4b38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395698"
---
# <a name="record-field-exchange-how-rfx-works"></a>记录字段交换：RFX 的工作方式

本主题解释了 RFX 过程。 这是一种高级主题，包括：

- [RFX 和记录集](#_core_rfx_and_the_recordset)

- [RFX 进程](#_core_the_record_field_exchange_process)

> [!NOTE]
>  本主题适用于从派生的类`CRecordset`中的批量行提取尚未实现。 如果使用批量行提取，实现批量记录字段交换 (Bulk RFX)。 批量 RFX 是类似于 RFX。 若要了解的差异，请参阅[记录集：(ODBC) 批量提取记录](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="_core_rfx_and_the_recordset"></a> RFX 和记录集

记录集对象的字段数据成员，集合在一起，组成一个编辑缓冲区，保存所选的列的一条记录。 当该记录集第一次打开并要读取的第一个记录时，RFX （关联） 每个选定列绑定到相应的字段数据成员的地址。 RFX 时记录集更新的记录，调用 ODBC API 函数来发送 SQL**更新**或**插入**向驱动程序的语句。 RFX 使用自身的字段数据成员的了解来指定要写入的列。

框架编辑缓冲区在备份某些阶段，因此必要时，它可以还原其内容。 RFX 备份编辑缓冲区，然后再添加一条新记录和之前编辑的现有记录。 它将在某些情况下，例如，编辑缓冲区还原后`Update`调用以下`AddNew`。 如果终止新更改的编辑缓冲区，例如，将移动到另一条记录，然后才能调用不会还原编辑缓冲区`Update`。

除了之间交换数据的数据源和记录集的字段数据成员，RFX 管理绑定参数。 当打开记录集时，任何参数数据成员绑定的顺序"？"中的 SQL 语句的占位符，`CRecordset::Open`构造。 有关详细信息，请参阅[记录集：参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

记录集类的重写的`DoFieldExchange`执行所有工作，在这两个方向上移动数据。 对话框数据交换 (DDX)，如 RFX 需要您的类数据成员的信息。 该向导提供所需的信息通过编写的记录集特定于实现`DoFieldExchange`，基于字段数据成员的名称和数据类型，指定使用向导。

##  <a name="_core_the_record_field_exchange_process"></a> 记录字段交换过程

本部分介绍 RFX 事件的顺序打开记录集对象时以及当您添加、 更新和删除记录。 该表[序列的 RFX 操作期间记录集开放](#_core_sequence_of_rfx_operations_during_recordset_open)和表[滚动过程中 RFX 操作的顺序](#_core_sequence_of_rfx_operations_during_scrolling)本主题中显示的进程作为 RFX 进程`Move`命令记录集和 RFX 管理更新。 在这些进程期间[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)调用来执行许多不同的操作。 `m_nOperation`的数据成员[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象确定请求的操作。 您可能会发现很有帮助读取[记录集：如何记录集选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)和[记录集：如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)在阅读本文之前。

###  <a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a> RFX:初始绑定的列和参数

以下 RFX 活动中所示，当您调用记录集对象的顺序发生[打开](../../mfc/reference/crecordset-class.md#open)成员函数：

- 如果记录集具有参数的数据成员，框架将调用`DoFieldExchange`将参数绑定到记录集的 SQL 语句字符串中的参数占位符。 在中找到的数据类型相关的表示形式参数的值用于每个占位符**选择**语句。 准备 SQL 语句之后但在执行之前，将发生这种情况。 有关语句准备的信息，请参阅`::SQLPrepare`ODBC 中的函数*程序员参考*。

- 框架将调用`DoFieldExchange`第二次将所选列的值绑定到记录集中的相应字段数据成员。 这会记录集对象建立为编辑缓冲区包含列的第一条记录。

- 记录集执行 SQL 语句，而数据源选择第一条记录。 记录的列加载到记录集的字段数据成员。

下表显示了 RFX 操作的顺序时打开记录集。

### <a name="_core_sequence_of_rfx_operations_during_recordset_open"></a> RFX 操作期间记录集已打开的顺序

|您的操作|DoFieldExchange 操作|数据库/SQL 操作|
|--------------------|-------------------------------|-----------------------------|
|1.打开记录集。|||
||2.生成 SQL 语句。||
|||3.发送 SQL。|
||4.绑定参数数据成员。||
||5.将字段数据成员绑定到列。||
|||6.ODBC 执行移动并填充的数据。|
||7.修复的数据C++。||

记录集使用 ODBC 的准备好的执行以允许进行快速再次查询使用相同的 SQL 语句。 准备好的执行有关的详细信息，请参阅 ODBC SDK*程序员参考*MSDN 库中。

###  <a name="_mfc_rfx.3a_.scrolling"></a> RFX:滚动

您从一条记录滚动到另一个时，框架将调用`DoFieldExchange`来替换以前存储在具有新记录的值的字段数据成员的值。

当用户移动记录，则下表显示了 RFX 操作的顺序。

### <a name="_core_sequence_of_rfx_operations_during_scrolling"></a> 在滚动期间 RFX 操作顺序

|您的操作|DoFieldExchange 操作|数据库/SQL 操作|
|--------------------|-------------------------------|-----------------------------|
|1.调用`MoveNext`或其他移动功能之一。|||
|||2.ODBC 执行移动并填充的数据。|
||3.修复的数据C++。||

###  <a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a> RFX:添加新记录和编辑现有记录

如果添加新记录，记录集进行操作作为编辑缓冲区以生成新的记录的内容。 与添加记录，编辑记录涉及更改记录集的字段数据成员的值。 RFX 角度来看，从序列如下所示：

1. 对记录集的调用[AddNew](../../mfc/reference/crecordset-class.md#addnew)或[编辑](../../mfc/reference/crecordset-class.md#edit)成员函数将导致 RFX 来存储当前编辑缓冲区，因此可以稍后能还原。

1. `AddNew` 或`Edit`准备编辑缓冲区中的字段，以便 RFX 可以检测已更改的字段数据成员。

   因为新记录都没有以前的值进行比较，使用新的`AddNew`将每个字段数据成员的值设置为 PSEUDO_NULL 值。 随后，当您调用`Update`，RFX PSEUDO_NULL 值的每个数据成员的值进行比较。 如果没有区别，已设置的数据成员。 (PSEUDO_NULL 不具有，则返回 true 的 Null 值的记录列相同，也不是其中一种与相同C++为 NULL。)

   与不同`Update`寻求`AddNew`，则`Update`寻求`Edit`进行比较，使用以前存储的值，而不是使用 PSEUDO_NULL 更新值。 不同之处在于`AddNew`没有以前存储的值进行比较。

1. 你想要编辑其值或你想提供新记录已填充，直接设置字段数据成员的值。 这可以包括调用`SetFieldNull`。

1. 对调用[更新](../../mfc/reference/crecordset-class.md#update)检查已更改的字段数据成员，如步骤 2 中所述 (请参阅表[滚动过程中 RFX 操作的顺序](#_core_sequence_of_rfx_operations_during_scrolling))。 如果都未发生更改，`Update`返回 0。 如果某些字段数据成员已更改，`Update`准备并执行 SQL**插入**包含记录中的所有更新的字段的值的语句。

1. 有关`AddNew`，`Update`通过还原以前存储的记录之前的当前值到结束`AddNew`调用。 有关`Edit`，新的已编辑值保持不变。

下表显示了 RFX 操作的顺序时添加一条新记录或编辑现有记录。

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>RFX 在 AddNew 和编辑过程的操作顺序

|您的操作|DoFieldExchange 操作|数据库/SQL 操作|
|--------------------|-------------------------------|-----------------------------|
|1.调用`AddNew`或`Edit`。|||
||2.备份编辑缓冲区。||
||3.有关`AddNew`、 将标记为"全新"的字段数据成员和 Null。||
|4.将值分配给记录集字段数据成员。|||
|5.调用 `Update`。|||
||6.检查已更改的字段。||
||7.生成 SQL**插入**语句`AddNew`或**更新**语句`Edit`。||
|||8。发送 SQL。|
||9.有关`AddNew`，编辑缓冲区还原到其备份内容。 有关`Edit`，删除备份。||

### <a name="rfx-deleting-existing-records"></a>RFX:删除现有记录

删除一条记录时，RFX 所有的字段设置为 NULL，删除记录，并且你必须将其移走提醒。 不需要任何其他 RFX 序列信息。

## <a name="see-also"></a>请参阅

[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[宏、 全局函数和全局变量](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange 类](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)