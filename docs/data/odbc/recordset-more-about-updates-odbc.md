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
ms.openlocfilehash: 955b26137ce976514d84f95f4d819779b93bd78a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368679"
---
# <a name="recordset-more-about-updates-odbc"></a>记录集：有关更新的更多信息 (ODBC)

本主题适用于 MFC ODBC 类。

本主题介绍：

- [其他操作（如事务）如何影响更新](#_core_how_transactions_affect_updates)。

- [您的更新和其他用户的更新](#_core_your_updates_and_the_updates_of_other_users)。

- [有关更新和删除成员函数](#_core_more_about_update_and_delete)的详细信息。

> [!NOTE]
> 本主题适用于从 `CRecordset` 派生的对象，其中尚未实现批量提取行。 如果已实现批量行提取，则某些信息不适用。 例如，`AddNew`您不能调用 、和`Edit``Delete``Update`成员函数;因此，不能调用 、和但是，您可以执行事务。 有关批量行提取的详细信息，请参阅[记录集：批量提取记录 （ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="how-other-operations-affect-updates"></a><a name="_core_how_other_operations_affect_updates"></a>其他操作如何影响更新

更新受更新时生效的事务、在完成事务之前关闭记录集以及完成事务之前滚动的影响。

### <a name="how-transactions-affect-updates"></a><a name="_core_how_transactions_affect_updates"></a>事务如何影响更新

除了了解`AddNew`如何`Edit`、`Delete`和 工作`BeginTrans`之外，了解[CDatabase](../../mfc/reference/cdatabase-class.md)和`Rollback`成员函数如何`CommitTrans`使用[CRecordset](../../mfc/reference/crecordset-class.md)的更新函数也很重要。

默认情况下，调用`AddNew`和`Edit`影响数据源时，您调用`Update`。 `Delete`呼叫立即生效。 但是，您可以建立事务并执行一批此类调用。 在提交更新之前，更新不是永久性的。 如果您改变主意，您可以回滚事务，而不是提交它。

有关交易记录的详细信息，请参阅事务[（ODBC）](../../data/odbc/transaction-odbc.md)。

### <a name="how-closing-the-recordset-affects-updates"></a><a name="_core_how_closing_the_recordset_affects_updates"></a>关闭记录集如何影响更新

如果关闭记录集或其关联`CDatabase`对象，事务正在进行中（您尚未调用[CDatabase：：CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)或[CDatabase：：回滚](../../mfc/reference/cdatabase-class.md#rollback)），则事务将自动回滚（除非您的数据库后端是 Microsoft Jet 数据库引擎）。

> [!CAUTION]
> 如果使用 Microsoft Jet 数据库引擎，则关闭显式事务中的记录集不会导致释放在提交或回滚显式事务之前已修改的任何行或已放置的锁。 建议您始终在显式 Jet 事务内外打开和关闭记录集。

### <a name="how-scrolling-affects-updates"></a><a name="_core_how_scrolling_affects_updates"></a>滚动如何影响更新

当您[记录集：在记录集中滚动 （ODBC） 时](../../data/odbc/recordset-scrolling-odbc.md)，编辑缓冲区将填充每个新的当前记录（不会首先存储以前的记录）。 滚动跳过以前删除的记录。 `AddNew`如果在 未`Edit`调用 或 调用后`Update`滚动`CommitTrans`而不调用`Rollback`，或第一次，则当新记录被引入编辑缓冲区时，任何更改都将丢失（无需警告）。 编辑缓冲区将填充滚动到的记录，释放存储的记录，并且数据源上不会发生任何更改。 这适用于 `AddNew` 和 `Edit`。

## <a name="your-updates-and-the-updates-of-other-users"></a><a name="_core_your_updates_and_the_updates_of_other_users"></a>您的更新和其他用户的更新

当您使用记录集更新数据时，更新会影响其他用户。 同样，在记录集的生存期内其他用户的更新也会影响您。

在多用户环境中，其他用户可以打开包含您在记录集中选择的某些相同记录集的记录集。 检索记录之前对记录的更改将反映在记录集中。 由于每次滚动到记录时，动态集都会检索记录，因此每次滚动到记录时，动态集都会反映更改。 快照在首次滚动到记录时检索记录，因此快照仅反映最初滚动到记录之前发生的更改。

除非重新查询，否则其他用户在打开记录集后添加的记录不会显示在记录集中。 如果记录集是动态集，则当您滚动到受影响的记录时，其他用户对现有记录进行编辑确实会显示在动态集中。 如果记录集是快照，则在重新查询快照之前不会显示编辑。 如果要查看快照中的其他用户添加或删除的记录，或者动态集中的其他用户添加的记录，请调用[CRecordset：：重新查询](../../mfc/reference/crecordset-class.md#requery)以重建记录集。 （请注意，其他用户的删除将显示在您的动态集中。您也可以打电话`Requery`查看您添加的记录，但不能查看您的删除内容。

> [!TIP]
> 要强制一次缓存整个快照，请立即在打开`MoveLast`快照后调用。 然后调用`MoveFirst`开始处理记录。 `MoveLast`等效于滚动所有记录，但它一次检索所有记录。 但是请注意，这可能会降低性能，并且某些驱动程序可能不需要这样做。

更新对其他用户的影响类似于它们对您的影响。

## <a name="more-about-update-and-delete"></a><a name="_core_more_about_update_and_delete"></a>有关更新和删除的详细信息

本节提供其他信息，以帮助您使用`Update`和`Delete`。

### <a name="update-success-and-failure"></a>更新成功和失败

如果`Update`成功，或`AddNew``Edit`模式将结束。 要再次开始`AddNew``Edit`或 模式，`AddNew`请`Edit`调用 或 。

如果`Update`失败（返回 FALSE 或引发异常），则保持`AddNew`或`Edit`模式，具体取决于您上次调用的函数。 你可以随后执行以下操作之一：

- 修改字段数据成员，然后`Update`重试。

- 调用`AddNew`将字段数据成员重置为 Null，设置字段数据成员的值，然后再次调用`Update`。

- 调用`Edit`以重新加载记录集中的值，然后再调用`AddNew`或`Edit`，设置字段数据成员的值，然后再次调用。 `Update` 成功`Update`调用后（`AddNew`呼叫后除外），字段数据成员将保留其新值。

- 调用`Move`（包括`Move`参数为 AFX_MOVE_REFRESH 或 0），该调用刷新任何更改并结束任何`AddNew`有效的`Edit`或模式。

### <a name="update-and-delete"></a>更新和删除

本节适用于`Update`和`Delete`。

在`Update`或`Delete`操作上，应更新一条记录和一条记录。 该记录是当前记录，对应于记录集字段中的数据值。 如果由于某种原因没有记录受到影响或多个记录受到影响，则引发包含以下**RETCODE**值之一的异常：

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

当引发这些异常时，您将`AddNew`处于调用`Edit``Update`或`Delete`时处于 或 状态。 下面是最常见的方案，在这些方案中您将看到这些异常。 您最有可能看到：

- AFX_SQL_ERROR_NO_ROWS_AFFECTED当您使用乐观锁定模式，而另一个用户已修改记录的方式，阻止框架识别要更新或删除的正确记录。

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED，当您正在更新的表没有主键或唯一索引时，并且记录集中没有足够的列来唯一标识表行。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：记录集如何选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[异常：数据库异常](../../mfc/exceptions-database-exceptions.md)
