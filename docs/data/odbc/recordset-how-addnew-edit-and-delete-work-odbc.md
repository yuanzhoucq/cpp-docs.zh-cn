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
ms.openlocfilehash: 13d4461833180b527fae153c1677c9e911fc2737
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620475"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>记录集：AddNew、Edit 和 Delete 的工作方式 (ODBC)

本主题适用于 MFC ODBC 类。

本主题介绍如何`AddNew`， `Edit`，并`Delete`类的成员函数`CRecordset`工作。 涵盖的主题包括：

- [如何添加记录的工作原理](#_core_adding_a_record)

- [添加的记录的可见性](#_core_visibility_of_added_records)

- [编辑记录的工作原理](#_core_editing_an_existing_record)

- [如何删除记录的工作原理](#_core_deleting_a_record)

> [!NOTE]
>  本主题适用于对象派生自`CRecordset`中的批量行提取尚未实现。 如果使用批量行提取，请参阅[记录集： 提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

作为补充，你可能想要读取[记录字段交换： RFX 的工作机制](../../data/odbc/record-field-exchange-how-rfx-works.md)，其中介绍了更新操作中的 RFX 相应角色。

##  <a name="_core_adding_a_record"></a> 添加一条记录

将新记录添加到记录集涉及调用记录集的[AddNew](../../mfc/reference/crecordset-class.md#addnew)成员函数，设置的值的新记录的字段数据成员，以及调用[更新](../../mfc/reference/crecordset-class.md#update)成员函数以写入与数据源记录。

作为调用的前提条件`AddNew`，记录集必须不能打开为只读的。 `CanUpdate`和`CanAppend`成员函数可用于确定这些条件。

当您调用`AddNew`:

- 存储编辑缓冲区中的记录，以便可以还原其内容，如果将取消该操作。

- 因此可以更高版本中检测更改，将标记的字段数据成员。 字段数据成员也被标记为清除 （未更改） 并将设置为 Null。

调用后`AddNew`、 编辑缓冲区表示新，准备好空记录，若要使用的值填充。 若要执行此操作，你手动设置的值通过将分配给它们。 而不是指定字段的实际数据值，可以调用`SetFieldNull`指定的值为 Null。

若要提交所做的更改，请调用`Update`。 当您调用`Update`提供新的记录：

- 如果您的 ODBC 驱动程序支持`::SQLSetPos`ODBC API 函数时，MFC 使用函数将记录添加数据源。 使用`::SQLSetPos`，MFC 可以更有效地地添加一条记录，因为它不包括构造和处理 SQL 语句。

- 如果`::SQLSetPos`不能使用，MFC 将执行以下操作：

    1.  如果检测不到任何更改，`Update`不执行任何操作，并返回 0。

    2.  如果有更改，`Update`构造 SQL**插入**语句。 中列出所有已更新字段数据成员所表示的列**插入**语句。 若要强制包含的列，请调用[SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty)成员函数：

        ```
        SetFieldDirty( &m_dataMember, TRUE );
        ```

    3.  `Update` 提交新记录 —**插入**执行语句并且该记录是提交到数据源 （如果不是快照，该记录集） 上的表，除非某个事务处于正在进行中。

    4.  已存储的记录将还原到编辑缓冲区。 记录之前的当前`AddNew`调用是当前再次无论**插入**成功执行语句。

    > [!TIP]
    >  新记录的完全控制，采用以下方法： 设置的任何字段，将具有值，然后显式设置将保持为 Null，通过调用任何字段的值`SetFieldNull`用一个指针指向字段并使用参数 TRUE （默认值）。 如果你想要确保字段不写入到数据源，调用`SetFieldDirty`用一个指针指向的字段和参数 FALSE，并且不要修改字段的值。 若要确定是否允许某个字段为 Null，请调用`IsFieldNullable`。

    > [!TIP]
    >  若要检测记录集数据成员更改值时，MFC，请使用适合于可以存储在记录集中每种数据类型的 PSEUDO_NULL 值。 如果您必须显式设置为 PSEUDO_NULL 值的字段和字段恰好已标记为 Null，则还必须调用`SetFieldNull`，第二个参数中的第一个参数和 FALSE 传入字段的地址。

##  <a name="_core_visibility_of_added_records"></a> 添加的记录的可见性

可见到记录集时添加的记录？ 已添加的记录有时显示，有时是不可见的具体取决于两件事：

- 支持的驱动程序。

- 哪些框架可以充分利用。

如果您的 ODBC 驱动程序支持`::SQLSetPos`ODBC API 函数时，MFC 使用函数以添加记录。 使用`::SQLSetPos`，添加记录会向任何可更新的 MFC 记录集。 不支持该函数，会增加记录不可见，则必须调用`Requery`才能看到它们。 使用`::SQLSetPos`更有效。

##  <a name="_core_editing_an_existing_record"></a> 编辑现有记录

编辑现有记录集中的记录涉及到该记录，调用记录集的滚动[编辑](../../mfc/reference/crecordset-class.md#edit)成员函数，设置的值的新记录的字段数据成员，以及调用[更新](../../mfc/reference/crecordset-class.md#update)成员函数以将更改的记录写入到数据源。

作为调用的前提条件`Edit`，记录集必须是可更新和上一条记录。 `CanUpdate`和`IsDeleted`成员函数可用于确定这些条件。 当前记录还必须已具有被删除，并且在记录集中必须记录 (同时`IsBOF`和`IsEOF`返回 0)。

当您调用`Edit`，编辑缓冲区 （当前记录） 中的记录存储。 存储的记录的值更高版本用于检测是否已更改的任何字段。

调用后`Edit`，编辑缓冲区仍表示当前记录，但现在已准备好接受对字段数据成员的更改。 若要更改的记录，手动设置任何你想要编辑的字段数据成员的值。 而不是指定字段的实际数据值，可以调用`SetFieldNull`指定的值为 Null。 若要提交所做的更改，请调用`Update`。

> [!TIP]
>  若要获取带`AddNew`或`Edit`模式，请调用`Move`与参数*AFX_MOVE_REFRESH*。

作为调用的前提条件`Update`、 记录集不能为空，并且必须尚未删除当前记录。 `IsBOF``IsEOF`，和`IsDeleted`都应返回 0。

当您调用`Update`的已编辑的记录：

- 如果您的 ODBC 驱动程序支持`::SQLSetPos`ODBC API 函数时，MFC 使用函数来更新数据源上的记录。 使用`::SQLSetPos`，驱动程序与在服务器上，如果两个不同更新服务器上的记录相应的记录将编辑缓冲区进行比较。 使用`::SQLSetPos`，MFC 可以更有效地更新的记录，因为它不包括构造和处理 SQL 语句。

     或

- 如果`::SQLSetPos`不能使用，MFC 将执行以下操作：

    1.  如果进行不了任何更改，`Update`不执行任何操作，并返回 0。

    2.  如果有更改，`Update`构造 SQL**更新**语句。 中列出的列**更新**语句基于已更改的字段数据成员。

    3.  `Update` 提交所做的更改 — 执行**更新**语句，并记录更改数据源，但时未提交的事务正在进行中 (请参阅[事务： 事务在执行记录集 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)事务如何影响更新有关的信息)。 ODBC 保留一份记录，这样也会更改。

    4.  与不同的过程`AddNew`，则`Edit`过程不会还原已存储的记录。 已编辑的记录将为当前记录保留在原位。

    > [!CAUTION]
    >  当你准备更新记录集通过调用`Update`，负责记录集，包含所有列的主键的表 （或所有表，任何唯一索引或足够多的列来唯一地标识行的列） 组成。 在某些情况下，框架可以使用仅选定为记录集中的列来标识表中要更新的记录。 不包含所有必要的列，可能会在表中更新多个记录。 在这种情况下，框架会引发异常时调用`Update`。

    > [!TIP]
    >  如果您调用`AddNew`或`Edit`以前，但之前您在调用这两种函数后调用`Update`，编辑缓冲区刷新与存储记录，替换为正在进行中的新建或编辑记录。 此行为，可以中止`AddNew`或`Edit`，并开始一个新： 如果你确定记录正在进行了故障，只需调用`Edit`或`AddNew`试。

##  <a name="_core_deleting_a_record"></a> 删除记录

滚动到该记录和记录集的调用从记录集删除记录涉及[删除](../../mfc/reference/crecordset-class.md#delete)成员函数。 与不同`AddNew`并`Edit`，`Delete`不需要匹配调用`Update`。

作为调用的前提条件`Delete`、 记录集必须可更新，并且它必须位于上一条记录。 `CanUpdate`， `IsBOF`， `IsEOF`，和`IsDeleted`成员函数可用于确定这些条件。

当您调用`Delete`:

- 如果您的 ODBC 驱动程序支持`::SQLSetPos`ODBC API 函数时，MFC 使用函数来删除数据源上的记录。 使用`::SQLSetPos`通常比使用 SQL 效率更高。

     或

- 如果`::SQLSetPos`不能使用，MFC 将执行以下操作：

    1.  编辑缓冲区中的当前记录不会备份作为 in`AddNew`和`Edit`。

    2.  `Delete` 构造 SQL**删除**中删除记录的语句。

         编辑缓冲区中的当前记录不会存储为在`AddNew`和`Edit`。

    3.  `Delete` 提交删除 — 执行**删除**语句。 该记录标记为已删除数据源和记录是快照，在 ODBC 中的。

    4.  已删除的记录的值仍在字段数据成员的记录集，但为 Null 和记录集的标记的字段数据成员`IsDeleted`成员函数返回一个非零值。

    > [!NOTE]
    >  删除一条记录后, 应该滚动到另一条记录来重新填充编辑缓冲区和新记录的数据。 它是调用错误`Delete`再次或调用`Edit`。

有关更新操作中使用的 SQL 语句的信息，请参阅[SQL](../../data/odbc/sql.md)。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：有关更新的更多信息 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)