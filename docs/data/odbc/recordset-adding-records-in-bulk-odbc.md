---
title: "记录集：批量添加记录 (ODBC) | Microsoft Docs"
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
  - "批量记录添加到记录集"
  - "ODBC 记录集, 添加记录"
  - "记录集, 添加记录"
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 记录集：批量添加记录 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 MFC [CRecordset](../../mfc/reference/crecordset-class.md) 类进行了新的优化，可提高成批向表中添加新记录的效率。  
  
> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，这些对象中尚未实现批量取行。  如果正在使用批量取行，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 当连续地添加多个记录但未调用 **Requery** 或 **Close** 时，[CRecordset::Open](../Topic/CRecordset::Open.md) 成员函数的 **dwOptions** 参数的新选项 **optimizeBulkAdd** 可提高性能。  仅有那些在第一次调用 **Update** 前是“已更新”的字段对于后续 `AddNew`\/**Update** 调用才被标记为“已更新”。  
  
 如果正在使用数据库类来利用 **::SQLSetPos** ODBC API 函数进行记录的添加、编辑和删除，则此优化是不必要的。  
  
 如果加载了 ODBC 游标库或者 ODBC 驱动程序不支持通过 **::SQLSetPos** 添加、编辑和删除，则此优化能提高批量添加性能。  若要打开此优化，请将记录集的 **Open** 调用中的 **dwOptions** 参数设置为：  
  
```  
appendOnly | optimizeBulkAdd  
```  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：添加、更新和删除记录 \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [记录集：锁定记录 \(ODBC\)](../../data/odbc/recordset-locking-records-odbc.md)