---
title: 事务：事务如何影响更新 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
ms.openlocfilehash: d03ec3f71c38f7790d66fbf6f800b7647e080147
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2019
ms.locfileid: "79544422"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>事务：事务如何影响更新 (ODBC)

对[数据源](../../data/odbc/data-source-odbc.md)的更新通过使用编辑缓冲区（与事务外部使用的方法相同）在事务期间进行管理。 记录集的字段数据成员统称为包含当前记录的编辑缓冲区，记录集在 `AddNew` 或 `Edit`期间临时备份。 在 `Delete` 操作期间，不会在事务中备份当前记录。 有关编辑缓冲区和更新如何存储当前记录的详细信息，请参阅[记录集：记录集如何更新记录（ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

> [!NOTE]
>  如果已实现批量行提取，则无法调用 `AddNew`、`Edit`或 `Delete`。 您必须编写自己的函数来对数据源执行更新。 有关批量行提取的详细信息，请参阅[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

在事务期间，可以提交或回滚 `AddNew`、`Edit`和 `Delete` 操作。 `CommitTrans` 和 `Rollback` 的影响可能会导致当前记录无法还原到编辑缓冲区。 若要确保正确还原当前记录，请务必了解 `CDatabase` 的 `CommitTrans` 和 `Rollback` 成员函数如何使用 `CRecordset`的更新函数。

##  <a name="how-committrans-affects-updates"></a><a name="_core_how_committrans_affects_updates"></a>CommitTrans 如何影响更新

下表说明了对事务 `CommitTrans` 的影响。

### <a name="how-committrans-affects-updates"></a>CommitTrans 如何影响更新

|Operation|数据源的状态|
|---------------|---------------------------|
|`AddNew` 和 `Update`，然后 `CommitTrans`|新记录被添加到数据源。|
|`AddNew` （不 `Update`），然后 `CommitTrans`|新记录丢失。 未将记录添加到数据源。|
|`Edit` 和 `Update`，然后 `CommitTrans`|已提交到数据源的编辑。|
|`Edit` （不 `Update`），然后 `CommitTrans`|对记录的编辑将丢失。 记录在数据源上保持不变。|
|然后 `Delete` `CommitTrans`|从数据源中删除的记录。|

##  <a name="how-rollback-affects-transactions"></a><a name="_core_how_rollback_affects_updates"></a>Rollback 如何影响事务

下表说明了对事务 `Rollback` 的影响。

### <a name="how-rollback-affects-transactions"></a>Rollback 如何影响事务

|Operation|当前记录的状态|还必须|数据源的状态|
|---------------|------------------------------|-------------------|---------------------------|
|`AddNew` 和 `Update`，然后 `Rollback`|暂时存储当前记录的内容，为新记录腾出空间。 新记录将进入编辑缓冲区。 调用 `Update` 后，当前记录将还原到编辑缓冲区。||与 `Update` 所做的数据源的补充相反。|
|`AddNew` （不 `Update`），然后 `Rollback`|暂时存储当前记录的内容，为新记录腾出空间。 编辑缓冲区包含新记录。|再次调用 `AddNew`，将编辑缓冲区还原为空的新记录。 或调用 `Move`（0）将旧值还原到编辑缓冲区。|由于未调用 `Update`，因此没有对数据源所做的更改。|
|`Edit` 和 `Update`，然后 `Rollback`|暂时存储当前记录的未编辑版本。 编辑缓冲区的内容。 调用 `Update` 后，仍会临时存储记录的未编辑版本。|*动态集*：向后滚动当前记录，然后返回以将未编辑的记录版本还原到编辑缓冲区。<br /><br /> *Snapshot*：调用 `Requery` 从数据源刷新记录集。|对 `Update` 所做的数据源所做的更改将会反转。|
|`Edit` （不 `Update`），然后 `Rollback`|暂时存储当前记录的未编辑版本。 编辑缓冲区的内容。|再次调用 `Edit`，将未编辑的记录版本还原到编辑缓冲区。|由于未调用 `Update`，因此没有对数据源所做的更改。|
|然后 `Delete` `Rollback`|删除当前记录的内容。|调用 `Requery` 从数据源还原当前记录的内容。|删除数据源中的数据。|

## <a name="see-also"></a>另请参阅

[事务 (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[事务：在记录集中执行事务 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[CDatabase 类](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)
