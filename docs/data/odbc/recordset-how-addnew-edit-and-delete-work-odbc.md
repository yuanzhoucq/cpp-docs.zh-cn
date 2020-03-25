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
ms.openlocfilehash: 8799ac36c443898f1e32b539f017e682bbf3e033
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212897"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>记录集：AddNew、Edit 和 Delete 的工作方式 (ODBC)

本主题适用于 MFC ODBC 类。

本主题说明类 `CRecordset` `AddNew`、`Edit`和 `Delete` 成员函数的工作方式。 涵盖的主题包括：

- [添加记录的工作方式](#_core_adding_a_record)

- [已添加记录的可见性](#_core_visibility_of_added_records)

- [编辑记录的工作原理](#_core_editing_an_existing_record)

- [删除记录的工作原理](#_core_deleting_a_record)

> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，其中尚未实现批量提取行。 如果使用批量取行，请参阅[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

作为补充，你可能需要读取[记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)，其中描述了 rfx 在更新操作中的相应角色。

##  <a name="adding-a-record"></a><a name="_core_adding_a_record"></a>添加记录

将新记录添加到记录集包括调用记录集的[AddNew](../../mfc/reference/crecordset-class.md#addnew)成员函数、设置新记录的字段数据成员的值，以及调用[更新](../../mfc/reference/crecordset-class.md#update)成员函数将记录写入数据源。

作为调用 `AddNew`的前提条件，记录集不得以只读方式打开。 `CanUpdate` 和 `CanAppend` 成员函数可让你确定这些条件。

调用 `AddNew`时：

- 将存储编辑缓冲区中的记录，因此，如果取消该操作，则可以还原其内容。

- 已对字段数据成员进行标记，以便以后可以检测它们中的更改。 字段数据成员也标记为 clean （未更改）并设置为 Null。

调用 `AddNew`后，编辑缓冲区表示一个新的空记录，准备好使用值填充。 若要执行此操作，请手动设置值，方法是将其分配给它们。 您可以调用 `SetFieldNull` 来指定 Null 值，而不是为字段指定实际数据值。

若要提交更改，请调用 `Update`。 为新记录调用 `Update` 时：

- 如果 ODBC 驱动程序支持 `::SQLSetPos` ODBC API 函数，则 MFC 将使用函数在数据源上添加记录。 使用 `::SQLSetPos`，MFC 可以更有效地添加记录，因为它不需要构造和处理 SQL 语句。

- 如果 `::SQLSetPos` 不能使用，MFC 会执行以下操作：

   1. 如果未检测到任何更改，`Update` 不执行任何操作并返回0。

   1. 如果有更改，`Update` 将构造 SQL **INSERT**语句。 所有已更新字段数据成员所表示的列都列在**INSERT**语句中。 若要强制包含列，请调用[SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty)成员函数：

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update` 提交新记录-将执行**INSERT**语句，并将记录提交到数据源（和记录集，如果不是快照）上的表，除非正在进行事务。

   1. 存储的记录将还原到编辑缓冲区。 无论**INSERT**语句是否已成功执行，当前 `AddNew` 调用之前的记录都是最新的。

   > [!TIP]
   > 若要完全控制新记录，请采用以下方法：设置包含值的任何字段的值，然后通过使用指向字段的指针和参数 TRUE （默认值），通过调用 `SetFieldNull` 来显式设置将保留 Null 的任何字段。 如果要确保字段未写入数据源，请使用指向字段的指针和参数 FALSE 调用 `SetFieldDirty`，而不会修改字段的值。 若要确定是否允许字段为 Null，请调用 `IsFieldNullable`。

   > [!TIP]
   > 为了在记录集数据成员更改值时进行检测，MFC 使用适用于你可以存储在记录集中的每个数据类型的 PSEUDO_NULL 值。 如果必须将字段显式设置为 PSEUDO_NULL 值并且该字段已标记为 Null，则还必须调用 `SetFieldNull`，同时在第一个参数中传递字段的地址，并在第二个参数中传递 FALSE。

##  <a name="visibility-of-added-records"></a><a name="_core_visibility_of_added_records"></a>已添加记录的可见性

添加记录对记录集可见的时间 添加的记录有时会显示，有时不会显示，具体取决于两个因素：

- 驱动程序的功能。

- 框架可以利用的功能。

如果 ODBC 驱动程序支持 `::SQLSetPos` ODBC API 函数，MFC 将使用函数来添加记录。 对于 `::SQLSetPos`，已添加的记录对任何可更新的 MFC 记录集都可见。 如果不支持该函数，则已添加的记录将不可见，因此必须调用 `Requery` 才能看到它们。 使用 `::SQLSetPos` 也更有效。

##  <a name="editing-an-existing-record"></a><a name="_core_editing_an_existing_record"></a>编辑现有记录

编辑记录集中的现有记录包括滚动到记录、调用记录集的[编辑](../../mfc/reference/crecordset-class.md#edit)成员函数、设置新记录的字段数据成员的值，以及调用[更新](../../mfc/reference/crecordset-class.md#update)成员函数以将更改的记录写入数据源。

作为调用 `Edit`的前提条件，记录集必须可更新和记录。 `CanUpdate` 和 `IsDeleted` 成员函数可让你确定这些条件。 当前记录也不能已被删除，并且记录集中必须有记录（`IsBOF` 和 `IsEOF` 返回0）。

调用 `Edit`时，将存储编辑缓冲区（当前记录）中的记录。 稍后将使用存储记录的值来检测是否有任何字段发生了更改。

调用 `Edit`后，编辑缓冲区仍表示当前记录，但现在可以接受对字段数据成员所做的更改。 若要更改记录，请手动设置要编辑的任何字段数据成员的值。 您可以调用 `SetFieldNull` 来指定 Null 值，而不是为字段指定实际数据值。 若要提交更改，请调用 `Update`。

> [!TIP]
> 若要退出 `AddNew` 或 `Edit` 模式，请调用 `Move` 参数*AFX_MOVE_REFRESH*。

作为调用 `Update`的前提条件，记录集不能为空，也不能删除当前记录。 `IsBOF`、`IsEOF`和 `IsDeleted` 都应返回0。

对已编辑记录调用 `Update` 时：

- 如果 ODBC 驱动程序支持 `::SQLSetPos` ODBC API 函数，MFC 将使用函数来更新数据源中的记录。 在 `::SQLSetPos`中，驱动程序将编辑缓冲区与服务器上的相应记录进行比较，如果这两个记录不同，则在服务器上更新记录。 使用 `::SQLSetPos`，MFC 可以更有效地更新记录，因为它不需要构造和处理 SQL 语句。

   \- 或 -

- 如果 `::SQLSetPos` 不能使用，MFC 会执行以下操作：

   1. 如果没有任何更改，`Update` 不执行任何操作并返回0。

   1. 如果有更改，`Update` 将构造一个 SQL **UPDATE**语句。 **UPDATE**语句中列出的列是基于已更改的字段数据成员的。

   1. `Update` 提交更改（执行**UPDATE**语句），并且记录在数据源上发生更改，但如果事务正在进行，则不提交该记录（请参阅[事务：在记录集中执行事务（ODBC）](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) ，了解有关事务如何影响更新的信息）。 ODBC 保存记录的副本，这也会发生更改。

   1. 与 `AddNew`的过程不同，`Edit` 进程不会还原存储的记录。 编辑后的记录将保留为当前记录。

   > [!CAUTION]
   > 当您准备通过调用 `Update`来更新记录集时，请注意您的记录集包括构成表的主键的所有列（或表中的所有唯一索引的所有列，或用于唯一标识该行的足够列）。 在某些情况下，框架只能使用记录集中所选的列来标识要更新的表中的记录。 如果没有所有必需的列，表中的多个记录可能会更新。 在这种情况下，在调用 `Update`时，框架会引发异常。

   > [!TIP]
   > 如果调用 `AddNew` 或 `Edit` 之后但在调用 `Update`之前调用了这两个函数，则会用存储的记录刷新编辑缓冲区，替换正在进行的新记录或编辑的记录。 此行为使你可以中止 `AddNew` 或 `Edit` 并开始一个新的操作：如果你确定正在进行的记录发生故障，只需再次调用 `Edit` 或 `AddNew`。

##  <a name="deleting-a-record"></a><a name="_core_deleting_a_record"></a>删除记录

从记录集中删除记录涉及到滚动到记录，以及调用记录集的[删除](../../mfc/reference/crecordset-class.md#delete)成员函数。 与 `AddNew` 和 `Edit`不同，`Delete` 不需要对 `Update`的匹配调用。

作为调用 `Delete`的前提条件，记录集必须可更新，并且它必须位于记录中。 `CanUpdate`、`IsBOF`、`IsEOF`和 `IsDeleted` 成员函数可让你确定这些条件。

调用 `Delete`时：

- 如果 ODBC 驱动程序支持 `::SQLSetPos` ODBC API 函数，MFC 将使用函数来删除数据源中的记录。 使用 `::SQLSetPos` 通常比使用 SQL 更有效。

   \- 或 -

- 如果 `::SQLSetPos` 不能使用，MFC 会执行以下操作：

   1. 不会像在 `AddNew` 和 `Edit`中那样备份编辑缓冲区中的当前记录。

   1. `Delete` 构造删除记录的 SQL **DELETE**语句。

      编辑缓冲区中的当前记录不作为 `AddNew` 和 `Edit`存储。

   1. `Delete` 提交删除-执行**DELETE**语句。 记录在数据源上标记为已删除，并且在 ODBC 中标记为快照。

   1. 已删除记录的值仍位于记录集的字段数据成员中，但字段数据成员标记为 Null，记录集的 `IsDeleted` 成员函数返回一个非零值。

   > [!NOTE]
   > 删除记录后，应滚动到其他记录，用新记录的数据重新填充编辑缓冲区。 再次调用 `Delete` 或调用 `Edit`是错误的。

有关更新操作中使用的 SQL 语句的详细信息，请参阅[sql](../../data/odbc/sql.md)。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：有关更新的更多信息 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)
