---
title: "记录集：书签和绝对位置 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SetAbsolutePosition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "绝对位置, ODBC 记录集"
  - "书签"
  - "书签, CDBVariant"
  - "书签, ODBC 记录集"
  - "CDBVariant 类, 书签"
  - "游标 [ODBC], 记录集内的绝对位置"
  - "GetBookmark 方法"
  - "ODBC 记录集, 绝对位置"
  - "ODBC 记录集, 书签"
  - "定位记录"
  - "记录定位"
  - "记录集, 绝对位置"
  - "记录集, 书签"
  - "SetAbsolutePosition 方法"
  - "SetAbsolutePosition 方法, 书签"
  - "SetBookmark 方法"
ms.assetid: 189788d6-33c1-41c5-9265-97db2a5d43cc
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 记录集：书签和绝对位置 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 在记录集中定位时常需要一种可以返回到特定记录的方法。  记录的书签和绝对位置提供两种这样的方法。  
  
 本主题说明：  
  
-   [如何使用书签](#_core_bookmarks_in_mfc_odbc)。  
  
-   [如何使用绝对位置设置当前记录](#_core_absolute_positions_in_mfc_odbc)。  
  
##  <a name="_core_bookmarks_in_mfc_odbc"></a> MFC ODBC 中的书签  
 一个书签唯一地标识一个记录。  在记录集中定位时，无法总是依赖记录的绝对位置，因为记录可以从记录集中删除。  跟踪记录位置的可靠方法是使用记录的书签。  `CRecordset` 类提供成员函数用于：  
  
-   获取当前记录的书签，以便可以将其保存在变量中 \([GetBookmark](../Topic/CRecordset::GetBookmark.md)\)。  
  
-   通过指定以前保存在变量中的书签快速移动到给定记录 \([SetBookmark](../Topic/CRecordset::SetBookmark.md)\)。  
  
 下面的示例说明如何使用这些成员函数标记当前记录并在以后返回到该记录：  
  
```  
// rs is a CRecordset or  
// CRecordset-derived object  
  
CDBVariant varRecordToReturnTo;  
rs.GetBookmark( varRecordToReturnTo );  
  
// More code in which you  
// move to other records  
  
rs.SetBookmark( varRecordToReturnTo );  
```  
  
 不必从 [CDBVariant Class](../../mfc/reference/cdbvariant-class.md)对象中提取基础数据类型。  用 `GetBookmark` 赋值并用 `SetBookmark` 返回到该书签。  
  
> [!NOTE]
>  根据 ODBC 驱动程序和记录集类型的不同，有可能不支持书签。  可以通过调用 [CRecordset::CanBookmark](../Topic/CRecordset::CanBookmark.md) 轻松地确定是否支持书签。  而且，如果支持书签，则必须显式选择通过指定 [CRecordset::Open](../Topic/CRecordset::Open.md) 成员函数中的 **CRecordset::useBookmarks** 选项来实现书签。  同时也应在某些记录集操作之后检查书签的持久性。  例如，如果 **Requery** 记录集，书签可能不再有效。  调用 [CDatabase::GetBookmarkPersistence](../Topic/CDatabase::GetBookmarkPersistence.md) 以检查是否可以安全地调用 `SetBookmark`。  
  
##  <a name="_core_absolute_positions_in_mfc_odbc"></a> MFC ODBC 中的绝对位置  
 除了书签外，`CRecordset` 类还允许通过指定序号位置来设置当前记录。  此序号位置称为绝对位置。  
  
> [!NOTE]
>  绝对位置在仅向前记录集中不可用。  有关仅向前记录集的更多信息，请参见[记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)。  
  
 若要使用绝对位置移动当前记录指针，请调用 [CRecordset::SetAbsolutePosition](../Topic/CRecordset::SetAbsolutePosition.md)。  向 `SetAbsolutePosition` 传递一个值后，与该序号位置对应的记录即成为当前记录。  
  
> [!NOTE]
>  记录的绝对位置有可能不可靠。  如果用户从记录集中删除记录，所有后续记录的序号位置都将更改。  建议使用书签的方法移动当前记录。  有关更多信息，请参见 [MFC ODBC 中的书签](#_core_bookmarks_in_mfc_odbc)。  
  
 有关记录集导航的更多信息，请参见[记录集：滚动 \(ODBC\)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)