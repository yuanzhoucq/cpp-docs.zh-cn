---
title: "记录集：有关更新的更多信息 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "多用户环境, 记录集的更新"
  - "ODBC 记录集, 更新"
  - "记录, 更新"
  - "记录集, 更新"
  - "滚动, 记录集的更新"
  - "事务, 更新记录集"
  - "更新记录集"
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集：有关更新的更多信息 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 本主题说明：  
  
-   [其他操作（如事务）对更新的影响](#_core_how_transactions_affect_updates)。  
  
-   [您的更新与其他用户的更新](#_core_your_updates_and_the_updates_of_other_users)。  
  
-   [有关更新与删除成员函数的更多内容](#_core_more_about_update_and_delete)。  
  
> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，这些对象中尚未实现批量取行。  如果已实现批量取行，则某些信息将不适用。  例如，不可调用 `AddNew`、**Edit**、**Delete** 及 **Update** 成员函数；但可执行事务。  有关批量取行的更多信息，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_how_other_operations_affect_updates"></a> 其他操作如何影响更新  
 更新受更新时有效的事务的影响，如完成事务之前关闭记录集和完成事务之前滚动都会影响更新。  
  
###  <a name="_core_how_transactions_affect_updates"></a> 事务如何影响更新  
 除了解 `AddNew`、**Edit** 及 **Delete** 的工作方式外，了解 [CDatabase](../../mfc/reference/cdatabase-class.md) 的 **BeginTrans**、**CommitTrans** 和 **Rollback** 成员函数如何处理 [CRecordset](../../mfc/reference/crecordset-class.md) 的更新函数也很重要。  
  
 默认情况下，调用 **Update** 后立即对 `AddNew` 与 **Edit** 进行调用将影响数据源。  **Delete** 调用立即生效。  但可建立一个事务并对这些调用执行批处理。  提交更新后更新才成为永久性的。  如果改变主意，可回滚事务而不是提交事务。  
  
 有关事务的更多信息，请参见[事务 \(ODBC\)](../../data/odbc/transaction-odbc.md)。  
  
###  <a name="_core_how_closing_the_recordset_affects_updates"></a> 关闭记录集如何影响更新  
 在事务正在进行时（尚未调用 [CDatabase::CommitTrans](../Topic/CDatabase::CommitTrans.md) 或 [CDatabase::Rollback](../Topic/CDatabase::Rollback.md)），如果关闭记录集或其关联的 `CDatabase` 对象，则事务将自动回滚（除非数据库后端是 Microsoft Jet 数据库引擎）。  
  
> [!CAUTION]
>  如果正在使用 Microsoft Jet 数据库引擎，则在显式事务提交或回滚之前，关闭显式事务中的记录集不会导致释放任何已修改的行和已放置的锁定。  建议始终在显式 Jet 事务的内部或外部打开与关闭记录集。  
  
###  <a name="_core_how_scrolling_affects_updates"></a> 滚动如何影响更新  
 在记录集中[记录集：滚动 \(ODBC\)](../../data/odbc/recordset-scrolling-odbc.md) 时，编辑缓冲区由每个新的当前记录填充（不先存储前一条记录）。  滚动跳过以前已删除的记录。  如果在 `AddNew` 或 **Edit** 调用之后未首先调用 **Update**、**CommitTrans** 或 **Rollback** 便进行滚动，则新的记录进入编辑缓冲区时将丢失任何更改（不发出警告）。  编辑缓冲区由滚至它的记录填充，已存储的记录被释放，数据源中未发生更改。  这种情况适用于 `AddNew` 与 **Edit**。  
  
##  <a name="_core_your_updates_and_the_updates_of_other_users"></a> 您的更新与其他用户的更新  
 当您使用记录集更新数据时，您的更新将影响其他用户。  同样，其他用户在您的记录集的生存期内所做的更新也将影响您。  
  
 在多用户环境中，其他用户可打开包含某些与您在您的记录集中选择的记录相同的记录集。  检索之前对记录所做的更改将在您的记录集中得到反映。  动态集在您每次滚至一个记录时检索该记录，因此动态集可在您每次滚至记录时反映更改。  快照在您第一次滚至一个记录时检索该记录，因此快照只能反映在您初次滚至该记录之前发生的更改。  
  
 除非您再次查询，否则在您打开记录集之后由其他用户添加的记录不会显示在您的记录集中。  如果您的记录集是动态集，则当您滚至受影响的记录时，其他用户对现有记录的编辑在您的动态集中可见。  如果您的记录集是快照，则在您再次查询快照时所做的编辑才可见。  如果想在您的快照中查看其他用户添加或删除的记录，或在您的动态集中查看其他用户添加的记录，则调用 [CRecordset::Requery](../Topic/CRecordset::Requery.md) 重新生成该记录集。（请注意，其他用户的删除在您的动态集中可见。）您也可以调用 **Requery** 查看您添加的记录，但不能查看您的删除。  
  
> [!TIP]
>  若要同时强制缓存整个快照，请在打开快照后立即调用 `MoveLast`。  然后调用 **MoveFirst** 开始处理记录。  `MoveLast` 等效于滚遍所有记录，但它同时检索所有记录。  但请注意，这可能会降低性能且可能不适用于某些驱动程序。  
  
 您的更新对其他用户的影响与其他用户的更新对您的影响相似。  
  
##  <a name="_core_more_about_update_and_delete"></a> 有关更新与删除的更多内容  
 本节为帮助您使用 **Update** 与 **Delete** 提供其他信息。  
  
### 更新成功与失败  
 如果 **Update** 成功，则 `AddNew` 或 **Edit** 模式结束。  若要再次开始 `AddNew` 或 **Edit** 模式，请调用 `AddNew` 或 **Edit**。  
  
 如果 **Update** 失败（返回 **FALSE** 或引发异常），则保持 `AddNew` 或 **Edit** 模式，具体取决于您最后调用的函数。  这时可执行下列操作之一：  
  
-   修改字段数据成员并再次调用 **Update**。  
  
-   调用 `AddNew` 将字段数据成员重置为 Null，设置字段数据成员的值，然后再次调用 **Update**。  
  
-   调用 **Edit** 重新加载第一次调用 `AddNew` 或 **Edit** 之前就已在记录集中的值，然后设置字段数据成员的值，之后再次调用 **Update**。  在 **Update** 调用成功之后（在 `AddNew` 调用后进行的调用除外），字段数据成员将保留其新值。  
  
-   调用 **Move**（包括带 **AFX\_MOVE\_REFRESH** 参数的 **Move** 或 0），它刷新所有更改并结束任何有效的 `AddNew` 或 **Edit** 模式。  
  
### 更新与删除  
 本节适用于 **Update** 与 **Delete**。  
  
 在 **Update** 或 **Delete** 操作中，一条且只有一条记录应被更新。  该记录是当前记录，它与记录集的字段中的数据值相对应。  如果因为某些原因没有记录受影响或多个记录受影响，则将引发包含下列某一 **RETCODE** 值的异常：  
  
-   **AFX\_SQL\_ERROR\_NO\_ROWS\_AFFECTED**  
  
-   **AFX\_SQL\_ERROR\_MULTIPLE\_ROWS\_AFFECTED**  
  
 这些异常引发时，您保持在调用 **Update** 或 **Delete** 时所处的 `AddNew` 或 **Edit** 状态。  以下是您将看到这些异常的最为常见的情景。  您最有可能看到：  
  
-   **AFX\_SQL\_ERROR\_NO\_ROWS\_AFFECTED** 当您正在使用开放式锁定模式，且另一个用户修改了记录，所采用的方式妨碍了框架标识要更新或删除的正确记录时。  
  
-   **AFX\_SQL\_ERROR\_MULTIPLE\_ROWS\_AFFECTED** 当您正在更新的表没有主键或唯一索引，且您在记录集中没有足够的列唯一标识表行时。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：记录集如何选择记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [记录字段交换 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)   
 [SQL](../../data/odbc/sql.md)   
 [异常：数据库异常](../../mfc/exceptions-database-exceptions.md)