---
title: 记录集：AddNew、Edit 和 Delete 的工作方式 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- AddNew method
- ODBC recordsets [C++], deleting records
- records [C++], deleting in recordsets
- data in recordsets [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
ms.openlocfilehash: 63718a6be3a9ce19ddbce923a84def21448c42a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367007"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>记录集：AddNew、Edit 和 Delete 的工作方式 (ODBC)

本主题适用于 MFC ODBC 类。

本主题介绍 类`AddNew``CRecordset``Edit`的`Delete`和 的成员函数的工作原理。 涵盖的主题包括：

- [添加记录的工作原理](#_core_adding_a_record)

- [已添加记录的可见性](#_core_visibility_of_added_records)

- [编辑记录的工作原理](#_core_editing_an_existing_record)

- [删除记录的工作原理](#_core_deleting_a_record)

> [!NOTE]
> 本主题适用于从 `CRecordset` 派生的对象，其中尚未实现批量提取行。 如果使用批量行提取，请参阅[记录集：批量提取记录 （ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

作为补充，您可能想要阅读[记录字段交换：RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)，它描述了 RFX 在更新操作中的相应作用。

## <a name="adding-a-record"></a><a name="_core_adding_a_record"></a>添加记录

向记录集添加新记录包括调用记录集的[AddNew](../../mfc/reference/crecordset-class.md#addnew)成员函数、设置新记录字段数据成员的值以及调用[Update](../../mfc/reference/crecordset-class.md#update)成员函数将记录写入数据源。

作为调用`AddNew`的先决条件，记录集不能作为只读打开。 `CanUpdate`和`CanAppend`成员函数允许您确定这些条件。

当您致电`AddNew`：

- 存储编辑缓冲区中的记录，因此，如果操作被取消，可以还原其内容。

- 字段数据成员将被标记，以便以后可以检测到其中的更改。 字段数据成员也标记为干净（未更改），并设置为 Null。

调用 后`AddNew`调用 ，编辑缓冲区表示新的空记录，准备用值填充。 为此，您可以通过分配给这些值来手动设置值。 可以调用`SetFieldNull`以指定值 Null，而不是为字段指定实际数据值。

要提交更改，请致电`Update`。 当您调用`Update`新记录时：

- 如果您的 ODBC 驱动程序支持`::SQLSetPos`ODBC API 函数，MFC 使用 该函数在数据源上添加记录。 使用`::SQLSetPos`MFC 可以更高效地添加记录，因为它不必构造和处理 SQL 语句。

- 如果`::SQLSetPos`无法使用，MFC 会执行以下操作：

   1. 如果未检测到任何更改，`Update`则不执行任何操作并返回 0。

   1. 如果存在更改，`Update`请构造 SQL **INSERT**语句。 由所有脏字段数据成员表示的列列在**INSERT**语句中列出。 要强制包含列，请调用[SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty)成员函数：

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update`提交新记录 - INSERT**语句执行**，记录将提交到数据源（以及记录集（如果不是快照）上的表，除非事务正在进行。

   1. 存储的记录将还原到编辑缓冲区。 无论 INSERT 语句是否成功`AddNew`执行，调用之前当前的记录都是再次**INSERT**最新的。

   > [!TIP]
   > 为了完全控制新记录，请采用以下方法：设置具有值的任何字段的值，然后通过调用指向字段和参数 TRUE（默认值）的指针显式`SetFieldNull`设置将保持为空的任何字段。 如果要确保字段未写入数据源，请使用指向字段和参数 FALSE 的`SetFieldDirty`指针调用，并且不修改字段的值。 要确定是否允许字段为 Null，请调用`IsFieldNullable`。

   > [!TIP]
   > 要检测记录组数据成员何时更改值，MFC 使用适合可存储在记录集中的每个数据类型的PSEUDO_NULL值。 如果必须显式将字段设置为PSEUDO_NULL值，并且该字段碰巧已标记为 Null，则还必须调用`SetFieldNull`，传递第一个参数中的字段地址，并在第二个参数中传递 FALSE。

## <a name="visibility-of-added-records"></a><a name="_core_visibility_of_added_records"></a>已添加记录的可见性

添加到的记录何时对记录集可见？ 添加的记录有时会显示，有时不可见，具体取决于两件事：

- 您的驱动程序能够做什么。

- 框架可以利用什么。

如果您的 ODBC 驱动程序支持`::SQLSetPos`ODBC API 功能，MFC 将使用该函数添加记录。 使用`::SQLSetPos`时，添加的记录对于任何可向上的 MFC 记录集都可见。 如果没有对函数的支持，添加的记录不可见，您必须调用`Requery`以查看它们。 使用`::SQLSetPos`效率也更高。

## <a name="editing-an-existing-record"></a><a name="_core_editing_an_existing_record"></a>编辑现有记录

编辑记录集中的现有记录包括滚动到记录、调用记录集的["编辑成员"](../../mfc/reference/crecordset-class.md#edit)函数、设置新记录的字段数据成员的值以及调用[Update](../../mfc/reference/crecordset-class.md#update)成员函数将更改的记录写入数据源。

作为调用`Edit`的先决条件，记录集必须是可备份的，并且是记录在案的。 `CanUpdate`和`IsDeleted`成员函数允许您确定这些条件。 当前记录也必须尚未删除，并且记录集中必须存在记录（和`IsBOF``IsEOF`返回 0）。

调用 时`Edit`，将存储编辑缓冲区（当前记录）中的记录。 存储的记录的值稍后用于检测是否有任何字段已更改。

调用`Edit`后，编辑缓冲区仍表示当前记录，但现在已准备好接受对字段数据成员的更改。 要更改记录，请手动设置要编辑的任何字段数据成员的值。 可以调用`SetFieldNull`以指定值 Null，而不是为字段指定实际数据值。 要提交更改，请致电`Update`。

> [!TIP]
> 要`AddNew`退出`Edit`或 模式，请`Move`使用 参数*AFX_MOVE_REFRESH*调用 。

作为调用`Update`的先决条件，记录集不能为空，并且当前记录不得被删除。 `IsBOF`，`IsEOF`并且`IsDeleted`应全部返回 0。

当您调用`Update`编辑的记录时：

- 如果您的 ODBC 驱动程序支持`::SQLSetPos`ODBC API 功能，MFC 将使用 该函数更新数据源上的记录。 使用`::SQLSetPos`，驱动程序会将编辑缓冲区与服务器上的相应记录进行比较，如果两者不同，则更新服务器上的记录。 使用`::SQLSetPos`MFC 可以更高效地更新记录，因为它不必构造和处理 SQL 语句。

   \- 或 -

- 如果`::SQLSetPos`无法使用，MFC 会执行以下操作：

   1. 如果没有更改，`Update`则不执行任何操作并返回 0。

   1. 如果存在更改，`Update`请构造 SQL **UPDATE**语句。 **UPDATE**语句中列出的列基于已更改的字段数据成员。

   1. `Update`提交更改 - 执行**UPDATE**语句 - 并在数据源上更改记录，但在事务正在进行时不会提交（请参阅[事务：在记录集 （ODBC） 中执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)，了解有关事务如何影响更新的信息。 ODBC 保留记录的副本，该副本也会更改。

   1. 与 的过程`AddNew`不同，`Edit`进程不还原存储的记录。 编辑的记录将保持当前记录的位置。

   > [!CAUTION]
   > 当您准备通过调用`Update`更新记录集时，请注意记录集包含组成表主键的所有列（或表上任何唯一索引的所有列，或足够列来唯一标识该行）。 在某些情况下，框架只能使用记录集中选择的列来标识要更新的表中的记录。 如果没有所有必要的列，则表中可能会更新多个记录。 在这种情况下，框架在调用`Update`时会引发异常。

   > [!TIP]
   > 如果以前`AddNew`调用或`Edit`调用任一函数，但在调用`Update`之前调用 ，则编辑缓冲区将刷新存储的记录，替换正在进行的新记录或已编辑的记录。 此行为为您提供了一种中止`AddNew`或`Edit`开始新记录的方法：如果您确定正在进行的记录有故障，只需调用或`Edit``AddNew`再次调用即可。

## <a name="deleting-a-record"></a><a name="_core_deleting_a_record"></a>删除记录

从记录集中删除记录涉及滚动到记录并调用记录集的["删除](../../mfc/reference/crecordset-class.md#delete)"成员函数。 与`AddNew``Edit`和`Delete`不同 ，不需要对`Update`的匹配调用。

作为调用`Delete`的先决条件，记录集必须是可向上的，并且必须在记录上。 、`CanUpdate``IsBOF``IsEOF`和`IsDeleted`成员函数允许您确定这些条件。

当您致电`Delete`：

- 如果您的 ODBC 驱动程序支持`::SQLSetPos`ODBC API 函数，MFC 将使用 该函数删除数据源上的记录。 使用`::SQLSetPos`通常比使用 SQL 更有效。

   \- 或 -

- 如果`::SQLSetPos`无法使用，MFC 会执行以下操作：

   1. 编辑缓冲区中的当前记录不备份为 和`AddNew``Edit`。

   1. `Delete`构造删除记录的 SQL **DELETE**语句。

      编辑缓冲区中的当前记录不存储为 和`AddNew``Edit`。

   1. `Delete`提交删除 = 执行**DELETE**语句。 记录在数据源上标记为已删除，如果记录是快照，则在 ODBC 中。

   1. 已删除的记录的值仍位于记录集的字段数据成员中，但字段数据成员标记为 Null，并且记录集`IsDeleted`的成员函数返回非零值。

   > [!NOTE]
   > 删除记录后，应滚动到另一条记录以用新记录的数据重新填充编辑缓冲区。 再次调用`Delete`或调用`Edit`是错误的。

有关更新操作中使用的 SQL 语句的信息，请参阅[SQL](../../data/odbc/sql.md)。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：有关更新的更多信息 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)
