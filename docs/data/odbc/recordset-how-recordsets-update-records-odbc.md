---
title: "记录集：记录集如何更新记录 (ODBC) | Microsoft Docs"
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
  - "ODBC 记录集, 更新"
  - "记录, 更新"
  - "记录集, 编辑记录"
  - "记录集, 更新"
  - "更新记录集"
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集：记录集如何更新记录 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 除能够从数据源选择记录外，记录集还可有选择地更新或删除选定的记录或添加新的记录。  有三个因素决定记录集的可更新能力：连接的数据源是否可更新、创建记录集对象时指定的选项以及已创建的 SQL。  
  
> [!NOTE]
>  `CRecordset` 对象所基于的 SQL 会影响记录集的更新能力。  例如，如果 SQL 包含联接或 **GROUP BY** 子句，则 MFC 将可更新能力设置为 **FALSE**。  
  
> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，这些对象中尚未实现批量取行。  如果正在使用批量取行，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 本主题说明：  
  
-   [您在记录集更新中的角色](#_core_your_role_in_recordset_updating)及框架为您完成的操作。  
  
-   [作为编辑缓冲区的记录集](#_core_the_edit_buffer)与[动态集与快照的区别](#_core_dynasets_and_snapshots)。  
  
 [记录集：AddNew、Edit 和 Delete 的工作方式 \(ODBC\)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) 从记录集的角度介绍这些函数的操作。  
  
 [记录集：有关更新的更多内容 \(ODBC\)](../../data/odbc/recordset-more-about-updates-odbc.md) 最后介绍记录集更新的其他方面，包括：说明事务是如何影响更新的，关闭记录集或滚动将如何影响正在进行的更新，以及您的更新如何与其他用户的更新交互。  
  
##  <a name="_core_your_role_in_recordset_updating"></a> 您在记录集更新中的角色  
 下表显示了您在使用记录集添加、编辑或删除记录中的角色，以及框架为您完成的操作。  
  
### 记录集更新：您与框架  
  
|你|框架|  
|-------|--------|  
|确定数据源是否可更新（或可追加）。|提供 [CDatabase](../../mfc/reference/cdatabase-class.md) 成员函数，用于测试数据源的更新能力或追加能力。|  
|打开可更新的记录集（可以为任何类型）。||  
|调用 `CRecordset` 更新函数（如 `CanUpdate` 或 `CanAppend`）确定记录集是否可更新。||  
|调用记录集成员函数添加、编辑及删除记录。|管理记录集对象与数据源之间交换数据的结构。|  
|还可以使用事务控制更新进程。|提供支持事务的 `CDatabase` 成员函数。|  
  
 有关事务的更多信息，请参见[事务 \(ODBC\)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="_core_the_edit_buffer"></a> 编辑缓冲区  
 记录集的字段数据成员共同作为编辑缓冲区，编辑缓冲区包含一个记录（即当前记录）。  更新操作使用该缓冲区操作当前记录。  
  
-   添加记录时，编辑缓冲区用于生成新的记录。  完成添加记录后，先前的当前记录再次成为当前记录。  
  
-   更新（编辑）记录时，编辑缓冲区用于将记录集的字段数据成员设置为新值。  完成更新后，更新后的记录仍为当前记录。  
  
 调用 [AddNew](../Topic/CRecordset::AddNew.md) 或 [Edit](../Topic/CRecordset::Edit.md) 时，当前记录被存储以便将来需要时还原。  调用 [Delete](../Topic/CRecordset::Delete.md) 时，当前记录并未存储而是标记为已删除，这时必须滚动到另一记录。  
  
> [!NOTE]
>  编辑缓冲区在记录删除操作中不起作用。  当您删除当前记录后，该记录被标记为已删除，且记录集为“没有记录”直到您滚动到另一记录为止。  
  
##  <a name="_core_dynasets_and_snapshots"></a> 动态集与快照  
 当滚动到某个记录时，[动态集](../../data/odbc/dynaset.md)将刷新该记录的内容。  [快照](../../data/odbc/snapshot.md)是记录的静态表示形式，因此除非调用 [Requery](../Topic/CRecordset::Requery.md)，否则不会刷新记录的内容。  若要使用动态集的所有功能，必须正使用符合正确的 ODBC API 支持级别的 ODBC 驱动程序。  有关更多信息，请参见 [ODBC](../../data/odbc/odbc-basics.md) 和[动态集](../../data/odbc/dynaset.md)。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：AddNew、Edit 和 Delete 的工作方式 \(ODBC\)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)