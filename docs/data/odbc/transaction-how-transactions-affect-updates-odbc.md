---
title: "事务：事务如何影响更新 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CommitTrans 方法"
  - "ODBC 记录集, 事务"
  - "Rollback 方法, ODBC 事务"
  - "事务, 回滚"
  - "事务, 更新记录集"
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 事务：事务如何影响更新 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在事务处理期间，对[数据源](../../data/odbc/data-source-odbc.md)的更新是通过使用编辑缓冲区管理的，方法与在事务外部使用的方法相同。  记录集的字段数据成员共同作为包含当前记录的编辑缓冲区。在 `AddNew` 或 **Edit** 期间，记录集暂时备份当前记录。  在 **Delete** 操作期间，当前记录不备份在事务内。  有关编辑缓冲区以及更新如何存储当前记录的更多信息，请参见 [记录集：记录集如何更新记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
> [!NOTE]
>  如果已实现批量取行，则不能调用 `AddNew`、**Edit** 或 **Delete**。  必须写自己的函数来执行对数据源的更新。  有关批量取行的更多信息，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 在事务处理期间，不能提交或回滚 `AddNew`、**Edit** 和 **Delete** 操作。  **CommitTrans** 和 **Rollback** 的影响可能会导致当前记录不能还原到编辑缓冲区中。  若要确保当前记录正确还原，了解 `CDatabase` 的 **CommitTrans** 和 **Rollback** 成员函数如何处理 `CRecordset` 的更新函数是很重要的。  
  
##  <a name="_core_how_committrans_affects_updates"></a> CommitTrans 如何影响更新  
 下表解释了 **CommitTrans** 对事务的影响。  
  
### CommitTrans 如何影响更新  
  
|Operation|数据源的状态|  
|---------------|------------|  
|`AddNew` 并 **Update**，然后 **CommitTrans**。|向数据源添加新记录。|  
|`AddNew`（无 **Update**），然后 **CommitTrans**。|新记录丢失。  记录不会被添加到数据源。|  
|**Edit** 并 **Update**，然后 **CommitTrans**。|向数据源提交编辑。|  
|**Edit**（无 **Update**），然后 **CommitTrans**|对记录的编辑丢失。  记录在数据源上保持不变。|  
|**Delete**，然后 **CommitTrans**|从数据源中删除记录。|  
  
##  <a name="_core_how_rollback_affects_updates"></a> Rollback 如何影响事务  
 下表解释了 **Rollback** 对事务的影响。  
  
### Rollback 如何影响事务  
  
|Operation|当前记录的状态|您还必须|数据源的状态|  
|---------------|-------------|----------|------------|  
|`AddNew` 并 **Update**，然后 **Rollback**|暂时存储当前记录的内容，以便为新记录腾出空位。  新记录输入到编辑缓冲区中。  在调用 **Update** 之后，当前记录还原到编辑缓冲区中。||撤消由 **Update** 对数据源进行的添加。|  
|`AddNew`（无 **Update**），然后 **Rollback**|暂时存储当前记录的内容，以便为新记录腾出空位。  编辑缓冲区包含新记录。|再次调用 `AddNew` 将编辑缓冲区还原到一个空的新记录。  或调用 **Move**\(0\) 将旧值还原到编辑缓冲区中。|因为未调用 **Update**，不对数据源进行更改。|  
|**Edit** 并 **Update**，然后 **Rollback**|暂时存储当前记录的未编辑版本。  对编辑缓冲区的内容进行编辑。  在调用 **Update** 之后，仍然暂时存储记录的未编辑版本。|*Dynaset*：滚过当前记录然后回滚，将记录的未编辑版本还原到编辑缓冲区中。<br /><br /> *Snapshot*：调用 **Requery** 从数据源刷新记录集。|撤消由 **Update** 对数据源进行的更改。|  
|**Edit**（无 **Update**），然后 **Rollback**|暂时存储当前记录的未编辑版本。  对编辑缓冲区的内容进行编辑。|再次调用 **Edit** 将记录的未编辑版本还原到编辑缓冲区中。|因为未调用 **Update**，不对数据源进行更改。|  
|**Delete**，然后 **Rollback**|删除当前记录的内容。|调用 **Requery** 从数据源还原当前记录的内容。|撤消从数据源进行的数据删除。|  
  
## 请参阅  
 [事务 \(ODBC\)](../../data/odbc/transaction-odbc.md)   
 [事务 \(ODBC\)](../../data/odbc/transaction-odbc.md)   
 [事务：在记录集中执行事务 \(ODBC\)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)