---
title: "记录集：滚动 (ODBC) | Microsoft Docs"
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
  - "Move 方法（记录集）"
  - "导航 [C++], 记录集"
  - "ODBC 记录集, 滚动"
  - "记录集 [C++], 开始"
  - "记录集 [C++], 结束"
  - "记录集 [C++], 移动到记录"
  - "记录集 [C++], 导航"
  - "滚动 [C++], 记录集"
ms.assetid: f38d2dcb-1e88-4e41-af25-98b00c276be4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集：滚动 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 打开记录集后，需要访问记录以显示值、进行计算、生成报表等。  滚动使您得以在记录集中的记录之间移动。  
  
 本主题说明：  
  
-   [从一个记录滚动到记录集中另一个记录的方式](#_core_scrolling_from_one_record_to_another)。  
  
-   [支持滚动和不支持滚动的情形](#_core_when_scrolling_is_supported)。  
  
##  <a name="_core_scrolling_from_one_record_to_another"></a> 从一个记录滚动到另一个记录  
 `CRecordset` 类提供 **Move** 成员函数用来在记录集中滚动。  这些函数按行集合移动当前记录。  如果已实现批量取行，则 **Move** 操作按行集合的大小重新定位记录集。  如果尚未实现批量取行，则对 **Move** 函数的调用按逐个记录重新定位记录集。  有关批量取行的更多信息，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
> [!NOTE]
>  通过记录集移动时，不能跳过已删除的记录。  有关更多信息，请参见 [IsDeleted](../Topic/CRecordset::IsDeleted.md) 成员函数。  
  
 除了 **Move** 函数外，`CRecordset` 还提供用来检查是否已滚动过记录集的结尾或开头的成员函数。  
  
 若要确定在记录集中是否可以滚动，请调用 `CanScroll` 成员函数。  
  
#### 滚动  
  
1.  向前滚动一条记录或一个行集合：调用 [MoveNext](../Topic/CRecordset::MoveNext.md) 成员函数。  
  
2.  向后滚动一条记录或一个行集合：调用 [MovePrev](../Topic/CRecordset::MovePrev.md) 成员函数。  
  
3.  移动到记录集中的第一条记录：调用 [moveFirst](../Topic/CRecordset::MoveFirst.md) 成员函数。  
  
4.  滚动到记录集中的最后一条记录或最后一个行集合：调用 [MoveLast](../Topic/CRecordset::MoveLast.md) 成员函数。  
  
5.  相对于当前位置的 *N* 条记录：调用 [Move](../Topic/CRecordset::Move.md) 成员函数。  
  
#### 测试是否已到记录集的结尾或开头  
  
1.  是否已滚过最后一条记录？  调用 [IsEOF](../Topic/CRecordset::IsEOF.md) 成员函数。  
  
2.  是否已滚出第一条记录（向后移动）？  调用 [IsBOF](../Topic/CRecordset::IsBOF.md) 成员函数。  
  
 下面的代码示例使用 `IsBOF` 和 `IsEOF` 检测在任一方向滚动时记录集的限制。  
  
```  
// Open a recordset; first record is current  
CCustSet rsCustSet( NULL );  
rsCustSet.Open( );  
  
if( rsCustSet.IsBOF( ) )  
    return;  
    // The recordset is empty  
  
// Scroll to the end of the recordset, past  
// the last record, so no record is current  
while ( !rsCustSet.IsEOF( ) )  
    rsCustSet.MoveNext( );  
  
// Move to the last record  
rsCustSet.MoveLast( );  
  
// Scroll to beginning of the recordset, before  
// the first record, so no record is current  
while( !rsCustSet.IsBOF( ) )  
    rsCustSet.MovePrev( );  
  
// First record is current again  
rsCustSet.MoveFirst( );  
```  
  
 如果将记录集定位在最后一条记录之后，则 `IsEOF` 返回一个非零值。  如果将记录集定位在第一条记录之前（所有记录之前），则 `IsBOF` 返回一个非零值。  两种情况下都没有要操作的当前记录。  如果在 `IsBOF` 已为 **TRUE** 时调用 `MovePrev`，或在 `IsEOF` 已为 **TRUE** 时调用 `MoveNext`，则框架引发 `CDBException`。  也可以使用 `IsBOF` 和 `IsEOF` 检查空记录集。  
  
 有关记录集导航的更多信息，请参见 [记录集：书签和绝对位置 \(ODBC\)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。  
  
##  <a name="_core_when_scrolling_is_supported"></a> 何时支持滚动  
 正如最初设计的，SQL 只提供向前滚动，而 ODBC 扩展了滚动功能。  滚动的可用支持级别取决于应用程序使用的 ODBC 驱动程序、驱动程序的 ODBC API 一致性级别，以及 ODBC 游标库是否加载到内存中。  有关更多信息，请参见 [ODBC](../../data/odbc/odbc-basics.md) 和 [ODBC：ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
> [!TIP]
>  可以控制是否使用游标库。  请参见 [CDatabase::Open](../Topic/CDatabase::Open.md) 的 `bUseCursorLib` 和 `dwOptions` 参数。  
  
> [!NOTE]
>  与 MFC DAO 类不同，MFC ODBC 类不提供用于定位符合指定条件的下一条记录（或前一条记录）的 **Find** 函数集。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::CanScroll](../Topic/CRecordset::CanScroll.md)   
 [CRecordset::CheckRowsetError](../Topic/CRecordset::CheckRowsetError.md)   
 [记录集：筛选记录 \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)