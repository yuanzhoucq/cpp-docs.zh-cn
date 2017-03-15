---
title: "记录集：锁定记录 (ODBC) | Microsoft Docs"
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
  - "数据 [C++], 锁定"
  - "锁定 [C++], 记录集"
  - "ODBC 记录集 [C++], 锁定记录"
  - "开放式锁定"
  - "开放式锁定, ODBC"
  - "ODBC 中的保守式锁定"
  - "记录集 [C++], 锁定记录"
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 记录集：锁定记录 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 本主题说明：  
  
-   [可用的记录锁定种类](#_core_record.2d.locking_modes)。  
  
-   [更新期间锁定记录集中的记录的方式](#_core_locking_records_in_your_recordset)。  
  
 使用记录集更新数据源上的数据时，应用程序可以锁定记录，这样其他用户就无法同时更新该记录。  由两个用户同时更新的记录的状态是未定义的，除非系统可以保证两个用户无法同时更新记录。  
  
> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，这些对象中尚未实现批量取行。  如果已实现批量取行，则某些信息将不适用。  例如，无法调用 **Edit** 和 **Update** 成员函数。  有关批量取行的更多信息，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_record.2d.locking_modes"></a> 记录锁定模式  
 数据库类提供两种[记录锁定模式](../Topic/CRecordset::SetLockingMode.md)：  
  
-   开放式锁定（默认）  
  
-   保守式锁定  
  
 更新记录需要三步：  
  
1.  通过调用 [Edit](../Topic/CRecordset::Edit.md) 成员函数开始操作。  
  
2.  更改当前记录的相应字段。  
  
3.  通过调用 [Update](../Topic/CRecordset::Update.md) 成员函数结束操作（并通常提交更新）。  
  
 开放式锁定仅在调用 **Update** 期间锁定数据源上的记录。  如果在多用户环境中使用开放式锁定，则应用程序将处理 **Update** 失败情况。  只要调用了 **Edit**，保守式锁定就锁定记录，直到调用 **Update** 时才释放记录（失败由 `CDBException` 机制指示，而不是通过 **Update** 返回的 **FALSE** 值指示）。  对于其他用户，保守式锁定有潜在的性能缺陷，因为它们对同一记录的并行访问可能必须要等到您的应用程序完成 **Update** 进程后才能进行。  
  
##  <a name="_core_locking_records_in_your_recordset"></a> 锁定记录集中的记录  
 如果要更改记录集对象的[锁定模式](#_core_record.2d.locking_modes)默认状态，则必须在调用 **Edit** 前更改此模式。  
  
#### 更改记录集的当前锁定模式  
  
1.  通过指定 **CRecordset::pessimistic** 或 **CRecordset::optimistic** 来调用 [SetLockingMode](../Topic/CRecordset::SetLockingMode.md) 成员函数。  
  
 新锁定模式在再次更改锁定模式或记录集关闭之前一直保持有效。  
  
> [!NOTE]
>  当前只有相对较少的 ODBC 驱动程序支持保守式锁定。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：执行联接 \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md)   
 [记录集：添加、更新和删除记录 \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)