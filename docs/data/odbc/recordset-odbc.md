---
title: "记录集 (ODBC) | Microsoft Docs"
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
  - "动态记录集"
  - "动态集"
  - "只能向前的记录集"
  - "ODBC 记录集"
  - "ODBC 记录集, CRecordset 对象"
  - "记录集, 关于记录集"
  - "记录集, 创建"
  - "记录集, 动态集"
  - "记录集, 快照"
  - "快照, ODBC 记录集"
ms.assetid: 333337c5-575e-4d26-b5f6-47166ad7874d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 [CRecordset](../../mfc/reference/crecordset-class.md) 对象表示从数据源选定的一组记录。  这些记录可以来自：  
  
-   表。  
  
-   查询。  
  
-   访问一个或多个表的存储过程。  
  
 基于表的记录集示例是“所有客户”，它访问一个“Customer”表。  查询的示例是“Joe Smith 的所有发票”。基于存储过程（有时称为预定义查询）的记录集示例是“所有过期的帐户”，它调用后端数据库中的存储过程。  记录集可以联接两个或更多来自同一数据源的表，但不能联接来自不同数据源的表。  
  
> [!NOTE]
>  有关用向导派生记录集类的信息，请参见[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)和 [MFC 应用程序向导的数据库支持](../../mfc/reference/database-support-mfc-application-wizard.md)。  
  
> [!NOTE]
>  某些 ODBC 驱动程序支持数据库视图。  从这种意义上说，视图是最初由 SQL `CREATE VIEW` 语句创建的查询。  向导目前不支持视图，但您自己可以通过编码实现该支持。  
  
##  <a name="_core_recordset_capabilities"></a> 记录集功能  
 所有记录集对象共享下列功能：  
  
-   如果数据源不是只读的，可以指定记录集为[可更新的](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)、[可追加的](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)或只读。  如果记录集是可更新的，只要驱动程序提供适当的锁定支持，就可以选择保守式或开放式[锁定](../../data/odbc/recordset-locking-records-odbc.md)方法。  如果数据源是只读的，则记录集也将是只读的。  
  
-   可以调用成员函数在选定的记录中 [Scroll](../../data/odbc/recordset-scrolling-odbc.md)。  
  
-   可以 [filter](../../data/odbc/recordset-filtering-records-odbc.md) 记录以限制从可用记录中选择的记录。  
  
-   可以基于一列或多列按升序或降序对记录进行 [Sort](../../data/odbc/recordset-sorting-records-odbc.md)。  
  
-   可以 [parameterize](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) 记录集以限定运行时记录集的选择。  
  
##  <a name="_core_snapshots_and_dynasets"></a> 快照和动态集  
 有两种主要的记录集：[快照](../../data/odbc/snapshot.md)和[动态集](../../data/odbc/dynaset.md)。  两者均由 `CRecordset` 类支持。  每一种都共享所有记录集的通用特性，但同时也以各自的专用方式扩展通用功能。  快照提供数据的静态视图，用于报表和需要数据视图在特定时间存在时的情况。  动态集则用于希望其他用户所做的更新在记录集中可见而同时又不必再次查询或刷新记录集的情况。  快照和动态集可以是可更新的，也可是只读的。  若要反映其他用户添加或删除的记录，请调用 [CRecordset::Requery](../Topic/CRecordset::Requery.md)。  
  
 `CRecordset` 还允许两种其他类型的记录集：动态记录集和仅向前记录集。  动态记录集类似于动态集；但动态记录集不用调用 `CRecordset::Requery` 就可以反映添加或删除的任何记录。  基于这个原因，动态记录集在 DBMS 上的处理时间方面通常成本较大，而且许多 ODBC 驱动程序不支持它们。  相比之下，仅向前记录集为不要求更新或向后滚动的记录集提供最有效的数据访问方法。  例如，可以使用仅向前记录集将记录从一个数据源移植到另一个数据源，其中只需按向前的方向在数据间移动。  若要使用仅向前记录集，必须执行下列两个操作：  
  
-   将 **CRecordset::forwardOnly** 选项作为 [Open](../Topic/CRecordset::Open.md) 成员函数的 `nOpenType` 参数传递。  
  
-   在 **Open** 的 `dwOptions` 参数中指定 **CRecordset::readOnly**。  
  
    > [!NOTE]
    >  有关 ODBC 驱动程序的动态集支持要求的信息，请参见 [ODBC](../../data/odbc/odbc-basics.md)。  有关 Visual C\+\+ 此版本中包括的 ODBC 驱动程序列表以及有关获取其他驱动程序的信息，请参见 [ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。  
  
##  <a name="_core_your_recordsets"></a> 您的记录集  
 对于希望访问的每一个不同的表、视图或存储过程，通常定义一个从 `CRecordset` 派生的类。（例外情况是数据库联接，其中一个记录集表示来自两个或多个表的列。）当派生记录集类时，启用记录字段交换 \(RFX\) 机制或批量记录字段交换（批量 RFX）机制，这两种机制与对话框数据交换 \(DDX\) 机制相似。  RFX 和“批量 RFX”简化了从数据源向您的记录集传输数据的过程；另外，RFX 还可以将数据从您的记录集传输到数据源。  有关更多信息，请参见[记录字段交换 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md) 和[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 记录集对象提供对所有选定记录的访问权。  使用 `CRecordset` 成员函数（如 `MoveNext` 和 `MovePrev`）在多个选定的记录间滚动。  同时，记录集对象仅表示一个选定的记录，即当前记录。  通过声明与表列或数据库查询产生的记录列相对应的记录集类成员变量，可以检查当前记录的字段。  有关记录集数据成员的信息，请参见[记录集：结构 \(ODBC\)](../../data/odbc/recordset-architecture-odbc.md)。  
  
 下列主题解释有关使用记录集对象的详细信息。  这些主题按功能类别和正常的浏览顺序列出，以便可以顺序阅读。  
  
### 有关打开、读取和关闭记录集的技巧的主题  
  
-   [记录集：结构 \(ODBC\)](../../data/odbc/recordset-architecture-odbc.md)  
  
-   [记录集：声明表的类 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)  
  
-   [记录集：创建和关闭记录集 \(ODBC\)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)  
  
-   [记录集：滚动 \(ODBC\)](../../data/odbc/recordset-scrolling-odbc.md)  
  
-   [记录集：书签和绝对位置 \(ODBC\)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)  
  
-   [记录集：筛选记录 \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)  
  
-   [记录集：对记录排序 \(ODBC\)](../../data/odbc/recordset-sorting-records-odbc.md)  
  
-   [记录集：参数化记录集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
### 有关修改记录集的技巧的主题  
  
-   [记录集：添加、更新和删除记录 \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)  
  
-   [记录集：锁定记录 \(ODBC\)](../../data/odbc/recordset-locking-records-odbc.md)  
  
-   [记录集：再次查询记录集 \(ODBC\)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)  
  
### 有关更高级的技术的主题  
  
-   [记录集：执行联接 \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md)  
  
-   [记录集：为预定义查询声明一个类 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)  
  
-   [记录集：动态绑定数据列 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)  
  
-   [记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)  
  
-   [记录集：处理大数据项 \(ODBC\)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)  
  
-   [记录集：获取 SUM 及其他聚合结果 \(ODBC\)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)  
  
### 有关记录集工作方式的主题  
  
-   [记录集：记录集如何选择记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)  
  
-   [记录集：记录集如何更新记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)  
  
## 请参阅  
 [开放式数据库连接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)   
 [MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [事务 \(ODBC\)](../../data/odbc/transaction-odbc.md)