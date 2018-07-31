---
title: 记录集： 有关详细信息更新 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9b781935a43c8ac4626385b5e2ea683f9c481978
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339622"
---
# <a name="recordset-more-about-updates-odbc"></a>记录集：有关更新的更多信息 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 本主题说明：  
  
-   [其他操作，例如事务如何影响更新](#_core_how_transactions_affect_updates)。  
  
-   [你的更新和其他用户](#_core_your_updates_and_the_updates_of_other_users)。  
  
-   [有关更新和删除成员函数的更多](#_core_more_about_update_and_delete)。  
  
> [!NOTE]
>  本主题适用于对象派生自`CRecordset`中的批量行提取尚未实现。 如果已实现批量行提取，某些信息不适用。 例如，不能调用`AddNew`， `Edit`， `Delete`，和`Update`成员函数; 但是，可以执行的事务。 有关批量行提取的详细信息，请参阅[记录集： 提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_how_other_operations_affect_updates"></a> 其他操作如何影响更新  
 你的更新会影响事务实际上在更新时，如完成事务之前关闭记录集和完成事务之前滚动。  
  
###  <a name="_core_how_transactions_affect_updates"></a> 事务如何影响更新  
 除了了解如何`AddNew`， `Edit`，并`Delete`工作，务必要了解如何`BeginTrans`， `CommitTrans`，和`Rollback`的成员函数[CDatabase](../../mfc/reference/cdatabase-class.md)适用于更新函数[CRecordset](../../mfc/reference/crecordset-class.md)。  
  
 默认情况下，调用`AddNew`并`Edit`影响的数据源时调用立即`Update`。 `Delete` 调用会立即生效。 但是，可以建立一个事务并执行此类调用的批处理。 提交它们才会永久更新。 如果你改变主意，可以回滚而不是提交事务。  
  
 有关事务的详细信息，请参阅[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
###  <a name="_core_how_closing_the_recordset_affects_updates"></a> 关闭记录集是如何影响更新  
 如果关闭记录集，或其关联`CDatabase`对象，其中包含一个事务正在进行中 (不调用了[CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)或[CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback))，回滚事务备份自动 （除非数据库后端为 Microsoft Jet 数据库引擎）。  
  
> [!CAUTION]
>  如果使用 Microsoft Jet 数据库引擎，关闭在显式事务内的记录集不会导致释放任何已修改的行或直到提交或回滚显式事务放置的锁。 建议该您始终同时打开和关闭记录集的内部或外部显式 Jet 事务。  
  
###  <a name="_core_how_scrolling_affects_updates"></a> 滚动如何影响更新  
 当您[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)在记录集中，编辑缓冲区填充与每个新的当前记录 （不先存储第一次一条记录）。 滚动跳过以前删除的记录。 如果向后滚动`AddNew`或`Edit`而无需调用调用`Update`， `CommitTrans`，或`Rollback`首先，任何更改都将丢失 （带您任何警告） 为一个新的记录放入编辑缓冲区。 编辑缓冲区填充与滚动到的记录、 已存储的记录将被释放，和数据源中未发生更改。 这同时适用于`AddNew`和`Edit`。  
  
##  <a name="_core_your_updates_and_the_updates_of_other_users"></a> 你的更新和其他用户的更新  
 当使用记录集来更新数据时，你的更新将影响其他用户。 同样，其他用户的记录集的生存期内的更新会影响你。  
  
 在多用户环境中，其他用户可以打开包含某些已选择为记录集中的同一个记录的记录集。 你检索之前对记录的更改将反映在记录集。 动态集，滚动到它每次检索一条记录，因为动态集反映更改每个滚动到一条记录的时间。 快照检索记录以便快照反映仅这些更改之前您最初滚动到的记录发生的滚动到，第一次。  
  
 打开记录集后添加其他用户的记录根本不显示为记录集中除非重新执行查询。 如果记录集是动态集，编辑与现有记录的其他用户执行操作显示在您的动态集时滚动到受影响的记录。 如果记录集是快照，编辑之前再次查询快照不会显示。 如果你想要查看添加的记录或快照或在您的动态集，其他用户添加的记录中的其他用户删除调用[CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery)重新生成该记录集。 （请注意，在您的动态集中显示的其他用户删除。）您也可以调用`Requery`若要查看记录添加，但不是以查看您的删除。  
  
> [!TIP]
>  若要强制执行的一次性快照将整个缓存，请调用`MoveLast`后立即打开快照。 然后，调用`MoveFirst`要开始处理记录。 `MoveLast` 等效于滚动通过所有记录，但它同时检索它们。 但是，请注意，这可能会降低性能，且可能不需要的某些驱动程序。  
  
 对其他用户更新的影响都类似于对您的影响。  
  
##  <a name="_core_more_about_update_and_delete"></a> 有关 Update 和 Delete 的详细信息  
 本部分提供可帮助您使用的其他信息`Update`和`Delete`。  
  
### <a name="update-success-and-failure"></a>更新成功和失败  
 如果`Update`成功，`AddNew`或`Edit`模式结束。 若要开始`AddNew`或`Edit`试模式，请调用`AddNew`或`Edit`。  
  
 如果`Update`失败 （返回 FALSE 或引发异常），也可以保持`AddNew`或`Edit`模式，具体取决于哪个函数最后调用。 然后可以执行下列任一操作：  
  
-   修改字段数据成员，然后重`Update`试。  
  
-   调用`AddNew`重置为 Null 的字段数据成员，设置字段数据成员的值，然后调用`Update`试。  
  
-   调用`Edit`若要重新加载已对第一个调用之前记录集中的值`AddNew`或`Edit`，请设置字段数据成员的值，然后调用`Update`试。 成功后`Update`调用 (除非后`AddNew`调用)，字段数据成员保留其新值。  
  
-   调用`Move`(包括`Move`AFX_MOVE_REFRESH 或 0 的参数)，这会刷新任何更改并结束任何`AddNew`或`Edit`有效模式。  
  
### <a name="update-and-delete"></a>更新和删除  
 本部分适用于两者`Update`和`Delete`。  
  
 上`Update`或`Delete`操作，应更新一个且只有一个记录。 该记录是对应于记录集的字段中的数据值的当前记录。 如果由于某种原因，不会影响多个记录或受影响的任何记录，其中包含以下值之一，将引发异常**RETCODE**值：  
  
-   AFX_SQL_ERROR_NO_ROWS_AFFECTED  
  
-   AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED  
  
 当引发这些异常时，也可以保持`AddNew`或`Edit`调用时所处状态`Update`或`Delete`。 以下是最常见的方案将在其中查看这些异常。 您最有可能看到：  
  
-   AFX_SQL_ERROR_NO_ROWS_AFFECTED 时使用的乐观锁定模式和另一个用户已修改的记录的方式，阻止从标识要更新或删除的正确记录框架。  
  
-   AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED 时要更新的表没有主键或唯一索引和您没有足够的列中唯一标识表行的记录集。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 如何记录集选择记录 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [SQL](../../data/odbc/sql.md)   
 [异常：数据库异常](../../mfc/exceptions-database-exceptions.md)