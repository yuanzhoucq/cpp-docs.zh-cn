---
title: "事务 (ODBC) | Microsoft Docs"
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
  - "数据库 [C++], 事务"
  - "ODBC [C++], 事务"
  - "ODBC 记录集 [C++], 事务"
  - "ODBC 记录集 [C++], 更新"
  - "记录集 [C++], 事务"
  - "记录集 [C++], 更新"
  - "事务 [C++], MFC ODBC 类"
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 事务 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 事务是将一系列 [数据源](../../data/odbc/data-source-odbc.md)更新分组或分批的方法，以便在回滚事务时同时提交所有事务或者不提交任何事务。  如果不使用事务，数据源的更改将自动提交而不是按需提交。  
  
> [!NOTE]
>  不是所有的 ODBC 数据库驱动程序都支持事务。  调用 [CDatabase](../../mfc/reference/cdatabase-class.md) 或 [CRecordset](../../mfc/reference/crecordset-class.md) 对象的 `CanTransact` 成员函数，确定您的驱动程序是否支持给定数据库的事务。  请注意，`CanTransact` 不通知您数据源是否提供完全事务支持。  在 **CommitTrans** 和 **Rollback** 之后还必须调用 `CDatabase::GetCursorCommitBehavior` 和 `CDatabase::GetCursorRollbackBehavior`，以检查事务在打开的 `CRecordset` 对象上的效果。  
  
 调用 **Update** 时，调用 `CRecordset` 对象的 `AddNew` 和 **Edit** 成员函数会立即影响数据源。  **Delete** 调用也立即生效。  相比之下，可以使用由多次 `AddNew`、**Edit**、**Update** 和 **Delete** 调用组成的事务，这些调用被执行，但直到显式调用 **CommitTrans** 时才提交。  通过建立事务，可以执行一系列这样的调用，同时保留使调用回滚的能力。  如果关键资源不可用或一些其他情况妨碍了整个事务的完成，可以回滚事务而不是提交事务。  在回滚事务时，属于事务的所有更改都不影响数据源。  
  
> [!NOTE]
>  目前，如果已实现批量取行，则 `CRecordset` 类不支持数据源更新。  这意味着不能调用 `AddNew`、**Edit**、**Delete** 或 **Update**。  但是，您可以编写自己的函数来执行更新，然后在给定的事务内调用那些函数。  有关批量取行的更多信息，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
> [!NOTE]
>  除了影响记录集外，事务还影响 SQL 语句，这些语句只要您使用与 `CDatabase` 对象关联的 ODBC **HDBC** 或使用基于该 **HDBC** 的 ODBC **HSTMT**，就会直接执行。  
  
 当有多个记录必须同时更新时，事务特别有用。  在这种情况下，您需要避免仅完成了一半的事务，例如当最后的更新完成前引发异常时所发生的事务。  将这些更新组成事务可以恢复（回滚）更改，使记录恢复到事务前的状态。  例如，如果银行将钱从帐户 A 转到帐户 B，从帐户 A 的提款和向帐户 B 的存款都必须正确地成功处理，否则整个事务必将失败。  
  
 在数据库类中，通过 `CDatabase` 对象执行事务。  `CDatabase` 对象表示到数据源的连接，与该 `CDatabase` 对象关联的一个或多个记录集通过记录集成员函数在数据库表上操作。  
  
> [!NOTE]
>  仅支持一个级别的事务。  事务不能嵌套，也不能跨多个数据库对象。  
  
 下列主题提供了有关如何执行事务的更多信息：  
  
-   [事务：在记录集中执行事务 \(ODBC\)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)  
  
-   [事务：事务如何影响更新 \(ODBC\)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)  
  
## 请参阅  
 [开放式数据库连接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)