---
title: 记录集：有关更新的更多信息 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
ms.openlocfilehash: f11c723e4589cb28a3f38100050a69a78fc0809e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212844"
---
# <a name="recordset-more-about-updates-odbc"></a>记录集：有关更新的更多信息 (ODBC)

本主题适用于 MFC ODBC 类。

本主题介绍：

- [其他操作（如事务）如何影响更新](#_core_how_transactions_affect_updates)。

- [你的更新和其他用户的更新](#_core_your_updates_and_the_updates_of_other_users)。

- [有关更新和删除成员函数的详细信息](#_core_more_about_update_and_delete)。

> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，其中尚未实现批量提取行。 如果已实现批量行提取，则某些信息不适用。 例如，你无法调用 `AddNew`、`Edit`、`Delete`和 `Update` 成员函数;不过，您可以执行事务。 有关批量行提取的详细信息，请参阅[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="how-other-operations-affect-updates"></a><a name="_core_how_other_operations_affect_updates"></a>其他操作对更新的影响

更新将受更新时有效的事务影响，方法是在完成事务前关闭记录集，然后在完成事务之前滚动。

###  <a name="how-transactions-affect-updates"></a><a name="_core_how_transactions_affect_updates"></a>事务如何影响更新

除了了解 `AddNew`、`Edit`和 `Delete` 的工作方式，务必要了解[CDatabase](../../mfc/reference/cdatabase-class.md)的 `BeginTrans`、`CommitTrans`和 `Rollback` 成员函数如何处理[CRecordset](../../mfc/reference/crecordset-class.md)的更新函数。

默认情况下，调用 `Update`时，对 `AddNew` 和 `Edit` 的调用将立即影响数据源。 `Delete` 调用会立即生效。 但你可以建立事务并执行一批此类调用。 在提交更新之前，不会永久更新。 如果改变主意，则可以回滚事务，而不是提交事务。

有关事务的详细信息，请参阅[Transaction （ODBC）](../../data/odbc/transaction-odbc.md)。

###  <a name="how-closing-the-recordset-affects-updates"></a><a name="_core_how_closing_the_recordset_affects_updates"></a>记录集如何影响更新

如果关闭了记录集或其关联的 `CDatabase` 对象，但事务正在进行中（尚未调用[cdatabase：： CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)或[Cdatabase：： Rollback](../../mfc/reference/cdatabase-class.md#rollback)），则事务会自动回滚（除非数据库后端是 Microsoft Jet 数据库引擎）。

> [!CAUTION]
>  如果使用的是 Microsoft Jet 数据库引擎，则关闭显式事务中的记录集不会导致释放已修改的任何行或在提交或回滚显式事务之前放置的锁。 建议始终在显式 Jet 事务内部或外部打开和关闭记录集。

###  <a name="how-scrolling-affects-updates"></a><a name="_core_how_scrolling_affects_updates"></a>滚动对更新的影响

当[记录集：滚动（ODBC）](../../data/odbc/recordset-scrolling-odbc.md)在记录集中时，将使用每个新的当前记录填充编辑缓冲区（前面的记录不会存储）。 滚动跳过以前删除的记录。 如果在不调用 `Update`、`CommitTrans`或 `Rollback` 的情况下，在 `AddNew` 或 `Edit` 调用之后滚动，则任何更改都将丢失（无任何警告），因为新记录将进入编辑缓冲区。 编辑缓冲区由滚动到的记录填充，存储的记录将被释放，并且不会在数据源上发生更改。 这同时适用于 `AddNew` 和 `Edit`。

##  <a name="your-updates-and-the-updates-of-other-users"></a><a name="_core_your_updates_and_the_updates_of_other_users"></a>你的更新和其他用户的更新

当您使用记录集更新数据时，您的更新会影响其他用户。 同样，在记录集的生存期内，其他用户的更新会影响你。

在多用户环境中，其他用户可以打开包含您在记录集中所选的一些相同记录的记录集。 在检索记录之前对记录所做的更改会反映在记录集中。 由于动态集会在每次滚动到该记录时检索记录，因此，每次滚动到一条记录时，动态集都会反映更改。 快照在第一次滚动到该记录时将检索记录，因此，快照仅反映在您最初滚动到记录之前所发生的更改。

在您打开记录集之后，其他用户添加的记录不会显示在您的记录集中，除非您重新查询。 如果记录集是动态集，则当滚动到受影响的记录时，其他用户对现有记录所做的编辑将显示在动态集中。 如果您的记录集是快照，则直到您重新查询快照时才会显示编辑。 如果要查看由快照中的其他用户添加或删除的记录，或者在动态集中的其他用户添加的记录，请调用[CRecordset：： Requery](../../mfc/reference/crecordset-class.md#requery)来重新生成记录集。 （请注意，其他用户的删除会显示在您的动态集中。）您还可以调用 `Requery` 以查看您添加的记录，但不能查看您的删除内容。

> [!TIP]
>  若要同时强制缓存整个快照，请在打开快照之后立即调用 `MoveLast`。 然后调用 `MoveFirst`，开始使用记录。 `MoveLast` 等效于滚动所有记录，但它同时检索所有记录。 但请注意，这可能会降低性能，某些驱动程序可能不需要这样做。

更新对其他用户的影响与它们对你的影响类似。

##  <a name="more-about-update-and-delete"></a><a name="_core_more_about_update_and_delete"></a>有关更新和删除的详细信息

本节提供其他信息来帮助你使用 `Update` 和 `Delete`。

### <a name="update-success-and-failure"></a>更新成功和失败

如果 `Update` 成功，则 `AddNew` 或 `Edit` 模式结束。 若要再次开始 `AddNew` 或 `Edit` 模式，请调用 `AddNew` 或 `Edit`。

如果 `Update` 失败（返回 FALSE 或引发异常），则将保持 `AddNew` 或 `Edit` 模式，具体取决于最后调用的函数。 你可以随后执行以下操作之一：

- 修改字段数据成员，然后重试 `Update`。

- 调用 `AddNew` 以将字段数据成员重置为 Null，设置字段数据成员的值，然后再次调用 `Update`。

- 调用 `Edit` 在首次调用 `AddNew` 或 `Edit`之前，重新加载记录集中的值，设置字段数据成员的值，然后再次调用 `Update`。 成功 `Update` 调用之后（`AddNew` 调用后除外），字段数据成员保留其新值。

- 调用 `Move` （包括 AFX_MOVE_REFRESH 参数为 `Move` 的或0），这会刷新任何更改并结束有效的所有 `AddNew` 或 `Edit` 模式。

### <a name="update-and-delete"></a>更新和删除

本部分适用于 `Update` 和 `Delete`。

在 `Update` 或 `Delete` 操作上，只应更新一条记录。 该记录是当前记录，对应于记录集的字段中的数据值。 如果由于某种原因不影响任何记录或多个记录受到影响，则会引发异常，其中包含以下**RETCODE**值之一：

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

在引发这些异常时，你将保留在调用 `Update` 或 `Delete`时所处 `AddNew` 或 `Edit` 状态。 下面是你将看到这些异常的最常见方案。 你最有可能看到：

- AFX_SQL_ERROR_NO_ROWS_AFFECTED 使用开放式锁定模式，而另一个用户已修改了记录，使框架无法识别要更新或删除的正确记录。

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED 如果您要更新的表没有主键或唯一索引，并且您在记录集中没有足够的列来唯一地标识表行。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：记录集如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[异常：数据库异常](../../mfc/exceptions-database-exceptions.md)
