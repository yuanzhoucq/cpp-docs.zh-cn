---
title: 事务： 事务如何影响更新 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e540b68b820234ee6d30295b40c7e0f4cb7c806d
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338585"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>事务：事务如何影响更新 (ODBC)
更新到[数据源](../../data/odbc/data-source-odbc.md)通过编辑缓冲区 （在事务外部使用的相同方法） 使用的事务处理期间管理。 记录集的字段数据成员共同作为包含记录集备份临时过程的当前记录的编辑缓冲区`AddNew`或`Edit`。 期间`Delete`事务内不备份操作，当前记录。 有关编辑缓冲区以及如何更新存储的当前记录的详细信息，请参阅[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
> [!NOTE]
>  如果已实现批量行提取，则不能调用`AddNew`， `Edit`，或`Delete`。 而是必须编写您自己的函数来执行与数据源的更新。 有关批量行提取的详细信息，请参阅[记录集： 提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 在事务期间`AddNew`， `Edit`，和`Delete`可以提交或回滚操作。 效果`CommitTrans`和`Rollback`可能会导致要还原为编辑缓冲区的当前记录。 为了确保正确还原当前记录，请务必了解如何`CommitTrans`并`Rollback`的成员函数`CDatabase`使用的更新函数`CRecordset`。  
  
##  <a name="_core_how_committrans_affects_updates"></a> CommitTrans 如何影响更新  
 下表说明的效果`CommitTrans`上的事务。  
  
### <a name="how-committrans-affects-updates"></a>CommitTrans 如何影响更新  
  
|操作|数据源的状态|  
|---------------|---------------------------|  
|`AddNew` 和`Update`，，然后 `CommitTrans`|新记录添加到数据源。|  
|`AddNew` (无需`Update`)，然后 `CommitTrans`|新的记录都将丢失。 不会添加到数据源的记录。|  
|`Edit` 和`Update`，，然后 `CommitTrans`|编辑已提交到数据源。|  
|`Edit` (无需`Update`)，然后 `CommitTrans`|编辑记录都将丢失。 记录在数据源保持不变。|  
|`Delete` 然后 `CommitTrans`|从数据源中删除的记录。|  
  
##  <a name="_core_how_rollback_affects_updates"></a> 回滚的事务影响  
 下表说明的效果`Rollback`上的事务。  
  
### <a name="how-rollback-affects-transactions"></a>回滚的事务影响  
  
|操作|当前记录的状态|你还必须|数据源的状态|  
|---------------|------------------------------|-------------------|---------------------------|  
|`AddNew` 和`Update`，然后 `Rollback`|当前记录的内容是临时存储，以便为新记录腾出。 新记录输入到编辑缓冲区。 之后`Update`调用时，当前记录还原为编辑缓冲区。||添加到数据源所做的`Update`反转。|  
|`AddNew` (无需`Update`)，然后 `Rollback`|当前记录的内容是临时存储，以便为新记录腾出。 编辑缓冲区包含新记录。|调用`AddNew`再次将还原到一个空的新记录的编辑缓冲区。 或调用`Move`(0) 以还原到编辑缓冲区的旧值。|因为`Update`未调用，没有对数据源所做的更改。|  
|`Edit` 和`Update`，然后 `Rollback`|临时存储的当前记录的未编辑的版本。 对编辑缓冲区的内容进行编辑。 之后`Update`调用时，未编辑的记录版本仍临时存储。|*动态集*： 滚过当前记录，然后返回到还原到编辑缓冲区未编辑的记录的版本。<br /><br /> *快照*： 调用`Requery`若要刷新数据源的记录集。|到数据源所做的更改`Update`进行了互换。|  
|`Edit` (无需`Update`)，然后 `Rollback`|临时存储的当前记录的未编辑的版本。 对编辑缓冲区的内容进行编辑。|调用`Edit`以还原到编辑缓冲区未编辑的记录的版本。|因为`Update`未调用，没有对数据源所做的更改。|  
|`Delete` 然后 `Rollback`|删除当前记录的内容。|调用`Requery`从数据源还原当前记录的内容。|撤消删除的数据源的数据。|  
  
## <a name="see-also"></a>请参阅  
 [事务 (ODBC)](../../data/odbc/transaction-odbc.md)   
 [事务 (ODBC)](../../data/odbc/transaction-odbc.md)   
 [事务： 在记录集 (ODBC) 执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)   
 [CDatabase 类](../../mfc/reference/cdatabase-class.md)   
 [CRecordset 类](../../mfc/reference/crecordset-class.md)