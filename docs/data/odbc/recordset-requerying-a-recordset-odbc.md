---
title: "记录集：再次查询记录集 (ODBC) | Microsoft Docs"
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
  - "ODBC 记录集, 再次查询"
  - "记录集, 再次查询"
  - "刷新记录集"
  - "Requery 方法"
  - "再次查询记录集"
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集：再次查询记录集 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 本主题介绍如何使用记录集对象从数据库再次查询（即刷新）其自身，以及何时可能要用 [Requery](../Topic/CRecordset::Requery.md) 成员函数执行此操作。  
  
 再次查询记录集的主要原因包括：  
  
-   使记录集在以下方面反映最新的更改：您或其他用户添加的记录，其他用户删除的记录。注意：您删除的记录已经反映在记录集中了。  
  
-   基于变化的参数值来刷新记录集。  
  
##  <a name="_core_bringing_the_recordset_up_to_date"></a> 使记录集是最新的  
 您经常要再次查询记录集对象以使记录集对象是最新的。  在多用户数据库环境中，其他用户可以在您的记录集的生存期内更改数据。  有关您的记录集何时反映其他用户所做的更改以及其他用户的记录集何时反映您所做的更改的更多信息，请参见[记录集：记录集如何更新记录 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) 和[动态集](../../data/odbc/dynaset.md)。  
  
##  <a name="_core_requerying_based_on_new_parameters"></a> 基于新参数再次查询  
 [Requery](../Topic/CRecordset::Requery.md) 的另一个常用（也是同等重要的）用法是基于变化的参数值选择一组新记录。  
  
> [!TIP]
>  如果用变化的参数值调用 **Requery**，则查询速度可能比再次调用 **Open** 快得多。  
  
##  <a name="_core_requerying_dynasets_vs.._snapshots"></a> 再次查询动态集与快照  
 由于动态集意味着用动态的最新数据表示记录集，因此，如果要反映其他用户的添加内容，则需要经常再次查询动态集。  另一方面，在准备报表、计算总数等操作时，快照的静态内容是非常安全的，因此快照也非常有用。  但是，某些时候可能也需要再次查询快照。  在多用户环境中，由于其他用户更改数据库，快照数据可能会与数据源失去同步。  
  
#### 再次查询记录集对象  
  
1.  调用对象的 [Requery](../Topic/CRecordset::Requery.md) 成员函数。  
  
 或者，可以关闭并重新打开原始记录集。  无论哪种情况，新记录集都代表数据源的当前状态。  
  
 有关示例，请参见[记录视图：从另一个记录集填充列表框](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)。  
  
> [!TIP]
>  若要优化 **Requery** 性能，请避免更改记录集的 [filter](../../data/odbc/recordset-filtering-records-odbc.md) 或 [Sort](../../data/odbc/recordset-sorting-records-odbc.md)。  在调用 **Requery** 前仅更改参数值。  
  
 如果 **Requery** 调用失败，可以重试调用，否则，应用程序应顺利终止。  对 **Requery** 或 **Open** 的调用可能会由于多种原因而失败。  可能由于发生了网络错误；或者在调用期间，在释放现有数据之后但尚未获得新数据之前，另一个用户可能获得独占性访问；或者记录集所依赖的表可能已被删除。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：动态绑定数据列 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [记录集：创建和关闭记录集 \(ODBC\)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)