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
ms.openlocfilehash: 8a87176ecb20beaf46583e1190b0ad458d508b31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376424"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>事务：事务如何影响更新 (ODBC)

数据源[的更新在](../../data/odbc/data-source-odbc.md)事务期间使用编辑缓冲区（与事务之外使用的方法相同）进行管理。 记录集的字段数据成员集体用作包含当前记录的编辑缓冲区，记录集在`AddNew`或`Edit`期间暂时备份该记录。 在`Delete`操作期间，当前记录不会在事务中备份。 有关编辑缓冲区和更新如何存储当前记录的详细信息，请参阅[记录集：记录集如何更新记录 （ODBC）。](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

> [!NOTE]
> 如果已实现批量行提取，则无法调用`AddNew`或`Edit`。 `Delete` 相反，您必须编写自己的函数才能对数据源执行更新。 有关批量行提取的详细信息，请参阅[记录集：批量提取记录 （ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

在事务期间`AddNew`，`Edit`可以提交`Delete`或回滚 和 操作。 的效果`CommitTrans``Rollback`可能会导致当前记录无法还原到编辑缓冲区。 为了确保正确还原当前记录，请务必`CommitTrans`了解 的`Rollback``CDatabase`和 成员函数如何使用`CRecordset`的更新函数。

## <a name="how-committrans-affects-updates"></a><a name="_core_how_committrans_affects_updates"></a>提交转换如何影响更新

下表解释了 对`CommitTrans`事务的影响。

### <a name="how-committrans-affects-updates"></a>提交转换如何影响更新

|Operation|数据源的状态|
|---------------|---------------------------|
|`AddNew`和`Update`，然后`CommitTrans`|新记录将添加到数据源中。|
|`AddNew`（没有`Update`），然后`CommitTrans`|新记录将丢失。 未添加到数据源的记录。|
|`Edit`和`Update`，然后`CommitTrans`|提交到数据源的编辑。|
|`Edit`（没有`Update`），然后`CommitTrans`|对记录的编辑将丢失。 在数据源上记录保持不变。|
|`Delete`然后`CommitTrans`|从数据源中删除的记录。|

## <a name="how-rollback-affects-transactions"></a><a name="_core_how_rollback_affects_updates"></a>回滚如何影响事务

下表解释了 对`Rollback`事务的影响。

### <a name="how-rollback-affects-transactions"></a>回滚如何影响事务

|Operation|当前记录的状态|您还必须|数据源的状态|
|---------------|------------------------------|-------------------|---------------------------|
|`AddNew`和`Update`，然后`Rollback`|当前记录的内容将暂时存储，以便为新记录腾出空间。 新记录将输入到编辑缓冲区中。 调用`Update`后，当前记录将还原到编辑缓冲区。||对所`Update`做数据源的添加是反向的。|
|`AddNew`（没有`Update`），然后`Rollback`|当前记录的内容将暂时存储，以便为新记录腾出空间。 编辑缓冲区包含新记录。|再次`AddNew`调用以将编辑缓冲区还原到空的新记录。 或调用`Move`（0） 将旧值还原到编辑缓冲区。|因为`Update`未调用，因此对数据源没有进行任何更改。|
|`Edit`和`Update`，然后`Rollback`|临时存储当前记录的未经编辑的版本。 编辑对编辑缓冲区的内容进行编辑。 调用`Update`后，记录的未编辑版本仍暂时存储。|*动态集*：滚动当前记录，然后返回以将未编辑的记录版本还原到编辑缓冲区。<br /><br /> *快照*：`Requery`调用从数据源刷新记录集。|对数据源`Update`所做的更改将发生逆转。|
|`Edit`（没有`Update`），然后`Rollback`|临时存储当前记录的未经编辑的版本。 编辑对编辑缓冲区的内容进行编辑。|再次`Edit`调用以将未编辑的记录版本还原到编辑缓冲区。|因为`Update`未调用，因此对数据源没有进行任何更改。|
|`Delete`然后`Rollback`|将删除当前记录的内容。|调用`Requery`从数据源还原当前记录的内容。|从数据源中删除数据将颠倒。|

## <a name="see-also"></a>另请参阅

[事务 (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[事务：在记录集中执行事务 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[CDatabase 类](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)
