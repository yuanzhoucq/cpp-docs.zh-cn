---
title: "记录集：创建和关闭记录集 (ODBC) | Microsoft Docs"
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
  - "ODBC 记录集, 关闭"
  - "ODBC 记录集, 创建"
  - "ODBC 记录集, 打开"
  - "记录集, 关闭"
  - "记录集, 创建"
  - "记录集, 打开"
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集：创建和关闭记录集 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 若要使用记录集，请构造记录集对象，然后调用该对象的 **Open** 成员函数来运行记录集的查询和选择记录。  完成记录集操作后，关闭并销毁记录集对象。  
  
 本主题说明：  
  
-   [何时以及如何创建记录集对象](#_core_creating_recordsets_at_run_time)。  
  
-   [何时以及如何通过参数化、筛选、排序或锁定来限定记录集的行为](#_core_setting_recordset_options)。  
  
-   [何时以及如何关闭记录集对象](#_core_closing_a_recordset)。  
  
##  <a name="_core_creating_recordsets_at_run_time"></a> 在运行时创建记录集  
 在程序中创建记录集对象之前，通常编写应用程序特定的记录集类。  有关此预备步骤的更多信息，请参见[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。  
  
 当需要从数据源选择记录时，打开动态集或快照对象。  要创建的对象类型取决于您要在应用程序中对数据进行的操作以及 ODBC 驱动程序支持的类型。  有关更多信息，请参见[动态集](../../data/odbc/dynaset.md)和[快照](../../data/odbc/snapshot.md)。  
  
#### 打开记录集  
  
1.  构造 `CRecordset` 派生的类的对象。  
  
     可以在堆或函数的堆栈帧上构造对象。  
  
2.  可以选择修改默认记录集行为。  有关可用选项，请参见[设置记录集选项](#_core_setting_recordset_options)。  
  
3.  调用对象的 [Open](../Topic/CRecordset::Open.md) 成员函数。  
  
 在该构造函数中，向 `CDatabase` 对象传递一个指针，或者传递 **NULL** 以使用框架将在 [GetDefaultConnect](../Topic/CRecordset::GetDefaultConnect.md) 成员函数返回的连接字符串的基础上构造并打开的临时数据库对象。  `CDatabase` 对象可能已连接到数据源。  
  
 对 **Open** 的调用使用 SQL 从数据源中选择记录。  选择的第一条记录（如果存在）为当前记录。  该记录的字段值存储在记录集对象的字段数据成员中。  如果选定了任何记录，则 `IsBOF` 和 `IsEOF` 成员函数都返回 0。  
  
 在 [Open](../Topic/CRecordset::Open.md) 调用中，可以：  
  
-   指定记录集是动态集还是快照。  默认情况下，记录集作为快照打开。  或者可以指定仅向前记录集，该记录集只允许向前逐个滚动记录。  
  
     默认情况下，记录集使用存储在 `CRecordset` 数据成员 **m\_nDefaultType** 中的默认类型。  向导写代码将 **m\_nDefaultType** 初始化为您在向导中选择的记录集类型。  如果不接受该默认设置，可以用另一种记录集类型替换。  
  
-   指定一个字符串来替换记录集构造的默认 SQL **SELECT** 语句。  
  
-   指定记录集是只读的还是仅追加的。  默认情况下，记录集允许完整更新；但可以限制该默认设置而只添加新记录，或者可以不允许所有的更新。  
  
 下面的示例显示如何打开 `CStudentSet` 类（一个应用程序特定的类）的只读快照对象：  
  
```  
// Construct the snapshot object  
CStudentSet rsStudent( NULL );  
// Set options if desired, then open the recordset  
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))  
    return FALSE;  
// Use the snapshot to operate on its records...  
```  
  
 调用 **Open** 后，使用该对象的成员函数和数据成员来处理记录。  某些情况下，可能需要再次查询或刷新记录集以包括数据源上已发生的更改。  有关更多信息，请参见[记录集：再次查询记录集 \(ODBC\)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)。  
  
> [!TIP]
>  开发期间使用的连接字符串可能和最终用户所需的连接字符串不同。  有关在这方面使您的应用程序通用的建议，请参见[数据源：管理连接 \(ODBC\)](../../data/odbc/data-source-managing-connections-odbc.md)。  
  
##  <a name="_core_setting_recordset_options"></a> 设置记录集选项  
 在构造记录集对象之后但尚未调用 **Open** 来选择记录之前，可能需要设置某些选项来控制记录集的行为。  对于所有记录集，可以：  
  
-   指定 [filter](../../data/odbc/recordset-filtering-records-odbc.md) 来限制记录的选定内容。  
  
-   指定记录的 [Sort](../../data/odbc/recordset-sorting-records-odbc.md) 顺序。  
  
-   指定 [Parameters](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)，以便可以使用运行时获得或计算出的信息来选择记录。  
  
 如果条件合适，还可以设置下面的选项：  
  
-   如果记录集是可更新的并支持锁定选项，则指定用于更新的[锁定](../../data/odbc/recordset-locking-records-odbc.md)方法。  
  
> [!NOTE]
>  若要影响记录的选择，必须在调用 **Open** 成员函数之前设置这些选项。  
  
##  <a name="_core_closing_a_recordset"></a> 关闭记录集  
 完成记录集操作后，必须释放记录集并解除分配其内存。  
  
#### 关闭记录集  
  
1.  调用其 [Close](../Topic/CRecordset::Close.md) 成员函数。  
  
2.  销毁记录集对象。  
  
     如果已经在函数的堆栈帧上声明该对象，则当该对象超出范围时自动被销毁。  否则，使用 **delete** 运算符。  
  
 **Close** 释放记录集的 **HSTMT** 句柄，  但不销毁 C\+\+ 对象。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：滚动 \(ODBC\)](../../data/odbc/recordset-scrolling-odbc.md)   
 [记录集：添加、更新和删除记录 \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)