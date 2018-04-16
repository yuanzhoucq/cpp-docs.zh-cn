---
title: "记录集： 有关详细信息更新 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1ad9042c4001fc1a0e0c8c8d19e5ac53b6312875
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-more-about-updates-odbc"></a>记录集：有关更新的更多信息 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 本主题说明：  
  
-   [其他操作，例如事务如何影响更新](#_core_how_transactions_affect_updates)。  
  
-   [你更新和其他用户的那些](#_core_your_updates_and_the_updates_of_other_users)。  
  
-   [有关更新和删除成员函数的详细信息](#_core_more_about_update_and_delete)。  
  
> [!NOTE]
>  本主题适用于派生自`CRecordset`中哪些批量行提取尚未实现。 如果你已实现批量行提取的某些信息不适用。 例如，不能调用`AddNew`，**编辑**，**删除**，和**更新**成员函数; 但是，你可以执行事务。 有关批量行提取的详细信息，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_how_other_operations_affect_updates"></a>其他操作如何影响更新  
 更新受事务实际上在的更新时，如完成事务之前关闭记录集和完成事务之前滚动。  
  
###  <a name="_core_how_transactions_affect_updates"></a>事务如何影响更新  
 超出了解如何`AddNew`，**编辑**，和**删除**工作，务必要了解如何**BeginTrans**， **CommitTrans**，和**回滚**的成员函数[CDatabase](../../mfc/reference/cdatabase-class.md)适用于的更新函数[CRecordset](../../mfc/reference/crecordset-class.md)。  
  
 默认情况下，调用到`AddNew`和**编辑**影响的数据源立即当调用**更新**。 **删除**调用会立即生效。 但你可以建立事务和执行此类调用一个批处理。 直到您提交这些更新不是永久的。 如果你改变主意，可以回滚而不是中提交事务。  
  
 有关事务的详细信息，请参阅[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
###  <a name="_core_how_closing_the_recordset_affects_updates"></a>关闭记录集如何影响更新  
 如果关闭记录集，或其关联`CDatabase`对象，具有正在进行的事务 (不调用了[CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)或[CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback))，回滚事务自动 （除非数据库后端是 Microsoft Jet 数据库引擎） 备份。  
  
> [!CAUTION]
>  如果你正在使用 Microsoft Jet 数据库引擎，关闭显式事务中的记录集不会导致释放任何已修改的行或直到显式事务是提交还是回滚放置的锁。 建议该你始终同时打开和关闭记录集的内部或外部的显式事务，Jet。  
  
###  <a name="_core_how_scrolling_affects_updates"></a>滚动如何影响更新  
 当你[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)在记录集中，编辑缓冲区充满 （不先存储前上一记录） 的每个新的当前记录。 滚动跳过以前删除的记录。 如果您向后滚动`AddNew`或**编辑**调用而不调用**更新**， **CommitTrans**，或**回滚**第一个，任何更改是一条新记录导入编辑缓冲区 （具有到你的任何警告） 丢失。 编辑缓冲区填充与滚动到的记录、 已存储的记录将被释放，和数据源中未发生更改。 这同时适用于`AddNew`和**编辑**。  
  
##  <a name="_core_your_updates_and_the_updates_of_other_users"></a>你更新和其他用户更新  
 当你使用记录集来更新数据时，更新会影响其他用户。 同样，其他用户的记录集的生存期内的更新会影响你。  
  
 在多用户环境中，其他用户可以打开记录集包含某些选择了记录集中的记录相同。 对你检索之前记录的更改将反映在你的记录集。 动态集检索记录滚动到每个时间，因为动态记录集反映到一条记录滚动，则每次更改。 快照检索记录以便快照反映仅发生之前你最初滚动到的记录这些更改滚动到它，第一次。  
  
 打开记录集之后，由其他用户添加的记录不会记录集中除非重新执行查询。 如果记录集是动态集，编辑由其他用户的现有记录是否显示在你的动态集中时滚动到受影响的记录。 如果你记录集是快照，编辑之前再次查询快照不会出现。 如果你想要看到记录添加或删除快照或在你的动态集中，其他用户添加的记录中的其他用户调用[CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery)重新生成的记录集。 （请注意，其他用户删除显示在您的动态集中。）您也可以调用**Requery**以查看记录添加，但不是以查看您的删除。  
  
> [!TIP]
>  若要强制的快照一次整个缓存，请调用`MoveLast`立即打开快照后。 然后调用**MoveFirst**若要开始使用记录。 `MoveLast`等效于滚动通过所有记录，但它在一次检索它们。 但请注意，这可能会降低性能并且可能不需要为某些驱动程序。  
  
 对其他用户的影响的更新都类似于对您的影响。  
  
##  <a name="_core_more_about_update_and_delete"></a>有关更新和删除的详细信息  
 本部分提供其他信息以帮助你使用的**更新**和**删除**。  
  
### <a name="update-success-and-failure"></a>更新成功和失败  
 如果**更新**成功，`AddNew`或**编辑**模式结束。 若要开始`AddNew`或**编辑**再次模式，请调用`AddNew`或**编辑**。  
  
 如果**更新**失败 (返回**FALSE**或引发异常)，将仍处于`AddNew`或**编辑**模式，具体取决于哪个函数最后调用。 然后，您可以执行以下任一操作：  
  
-   修改字段数据成员，并重试**更新**试。  
  
-   调用`AddNew`重置为 Null 的字段数据成员，设置字段数据成员的值，然后调用**更新**试。  
  
-   调用**编辑**重新加载的值对的第一个调用之前的记录集的`AddNew`或**编辑**，设置字段数据成员的值，然后调用**更新**试。 成功后**更新**调用 (除非后`AddNew`调用)，字段数据成员保留其新值。  
  
-   调用**移动**(包括**移动**其中参数**AFX_MOVE_REFRESH**，则为 0)，它会刷新任何更改并结束任何`AddNew`或**编辑**有效的模式。  
  
### <a name="update-and-delete"></a>更新和删除  
 本部分适用于**更新**和**删除**。  
  
 上**更新**或**删除**操作，应更新且只有一个记录。 该记录是当前记录，它对应于记录集的字段中的数据值。 如果由于某种原因不会影响多个记录或记录不会受到影响，将引发异常，包含以下项之一**某一 RETCODE**值：  
  
-   **AFX_SQL_ERROR_NO_ROWS_AFFECTED**  
  
-   **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED**  
  
 当引发这些异常时，将仍处于`AddNew`或**编辑**你调用时所处状态**更新**或**删除**。 以下是最常见的方案将在其中看到这些异常。 你最有可能看到：  
  
-   **AFX_SQL_ERROR_NO_ROWS_AFFECTED**时你正在使用乐观锁定模式和其他用户进行了修改以一种阻止 framework 标识正确的记录，若要更新或删除的记录。  
  
-   **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED**当你要更新的表具有没有主键或唯一索引和你没有足够多的列中为唯一标识表行的记录集。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 如何记录集选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [SQL](../../data/odbc/sql.md)   
 [异常：数据库异常](../../mfc/exceptions-database-exceptions.md)