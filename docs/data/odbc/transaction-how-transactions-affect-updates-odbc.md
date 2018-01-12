---
title: "事务： 事务如何影响更新 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 59eb8aecbf2dd2138c8a0469d71364b55fd82774
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>事务：事务如何影响更新 (ODBC)
更新到[数据源](../../data/odbc/data-source-odbc.md)通过编辑缓冲区 （在事务外部使用的相同方法） 使用的事务处理期间管理。 记录集的字段数据成员共同作为包含当前记录，记录集备份临时期间编辑缓冲区`AddNew`或**编辑**。 期间**删除**操作，当前记录不会备份在事务中。 有关编辑缓冲区以及如何更新存储的当前记录的详细信息，请参阅[记录集： 如何更新记录 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
> [!NOTE]
>  如果你已实现批量行提取，则无法调用`AddNew`，**编辑**，或**删除**。 你必须改为编写您自己的函数，对数据源执行更新。 有关批量行提取的详细信息，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 在事务处理，过程`AddNew`，**编辑**，和**删除**可以提交或回滚操作。 效果**CommitTrans**和**回滚**可能会导致不会还原到编辑缓冲区中的当前记录。 若要确保正确还原当前记录，务必要了解如何**CommitTrans**和**回滚**的成员函数`CDatabase`适用于更新函数`CRecordset`.  
  
##  <a name="_core_how_committrans_affects_updates"></a>CommitTrans 如何影响更新  
 下表说明带来的影响**CommitTrans**对中的事务。  
  
### <a name="how-committrans-affects-updates"></a>CommitTrans 如何影响更新  
  
|操作|数据源的状态|  
|---------------|---------------------------|  
|`AddNew`和**更新**，，然后**CommitTrans**|新的记录添加到数据源。|  
|`AddNew`(而无需**更新**)，然后**CommitTrans**|新的记录都将丢失。 不会添加到数据源的记录。|  
|**编辑**和**更新**，，然后**CommitTrans**|提交到数据源的编辑。|  
|**编辑**(而无需**更新**)，然后**CommitTrans**|对记录的编辑都将丢失。 记录在数据源上保持不变。|  
|**删除**然后**CommitTrans**|从数据源中删除的记录。|  
  
##  <a name="_core_how_rollback_affects_updates"></a>如何回滚影响事务  
 下表说明带来的影响**回滚**对中的事务。  
  
### <a name="how-rollback-affects-transactions"></a>如何回滚影响事务  
  
|操作|当前记录的状态|此外必须|数据源的状态|  
|---------------|------------------------------|-------------------|---------------------------|  
|`AddNew`和**更新**，然后**回滚**|暂时存储的当前记录的内容以释放空间用于新记录。 编辑缓冲区输入新的记录。 后**更新**调用时，当前记录还原为编辑缓冲区。||添加到数据源所做的**更新**已逆转。|  
|`AddNew`(而无需**更新**)，然后**回滚**|暂时存储的当前记录的内容以释放空间用于新记录。 编辑缓冲区包含新的记录。|调用`AddNew`再次将还原到一个空的新记录的编辑缓冲区。 或调用**移动**(0) 可还原到编辑缓冲区的旧值。|因为**更新**未调用，不没有对数据源进行任何更改。|  
|**编辑**和**更新**，然后**回滚**|临时存储的当前记录的原样的版本。 对编辑缓冲区的内容进行编辑。 后**更新**调用时，未编辑的记录的版本仍临时存储。|*动态集*： 滚过当前的记录，然后回来，以便还原到编辑缓冲区原样的版本的记录。<br /><br /> *快照*： 调用**Requery**刷新数据源的记录集。|到数据源所做的更改**更新**进行了互换。|  
|**编辑**(而无需**更新**)，然后**回滚**|临时存储的当前记录的原样的版本。 对编辑缓冲区的内容进行编辑。|调用**编辑**以还原到编辑缓冲区原样的版本的记录。|因为**更新**未调用，不没有对数据源进行任何更改。|  
|**删除**然后**回滚**|删除当前记录的内容。|调用**Requery**从数据源中还原当前记录的内容。|删除数据源的数据将被反转。|  
  
## <a name="see-also"></a>请参阅  
 [事务 (ODBC)](../../data/odbc/transaction-odbc.md)   
 [事务 (ODBC)](../../data/odbc/transaction-odbc.md)   
 [事务： 在记录集 (ODBC) 执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)   
 [CDatabase 类](../../mfc/reference/cdatabase-class.md)   
 [CRecordset 类](../../mfc/reference/crecordset-class.md)