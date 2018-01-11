---
title: "记录集： 书签和绝对位置 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SetAbsolutePosition
dev_langs: C++
helpviewer_keywords:
- CDBVariant class, bookmarks
- absolute positions, ODBC recordsets
- bookmarks, CDBVariant
- bookmarks, ODBC recordsets
- ODBC recordsets, absolute positions
- ODBC recordsets, bookmarks
- cursors [ODBC], absolute position in recordsets
- recordsets, bookmarks
- bookmarks
- SetAbsolutePosition method
- recordsets, absolute positions
- positioning records
- SetBookmark method
- record positioning
- GetBookmark method
- SetAbsolutePosition method, bookmarks
ms.assetid: 189788d6-33c1-41c5-9265-97db2a5d43cc
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4b206e5d09d86613af0585df7510b0f88397984a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>记录集：书签和绝对位置 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 导航时在记录集中，你经常需要一种方法将返回到特定的记录。 记录的书签和绝对位置提供两个此类方法。  
  
 本主题说明：  
  
-   [如何使用书签](#_core_bookmarks_in_mfc_odbc)。  
  
-   [如何设置使用绝对位置的当前记录](#_core_absolute_positions_in_mfc_odbc)。  
  
##  <a name="_core_bookmarks_in_mfc_odbc"></a>MFC ODBC 中的书签  
 书签唯一标识一条记录。 当你导航到记录集时，你无法始终依赖于一条记录的绝对位置因为可以从记录集中删除记录。 若要跟踪的一条记录的位置的可靠方式是使用其书签。 类`CRecordset`提供成员函数：  
  
-   获取当前记录，该书签，因此你可以将其保存在变量 ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark))。  
  
-   快速移动到给定的记录通过指定其前面在变量中保存的书签 ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark))。  
  
 下面的示例演示如何使用这些成员函数将当前记录标记并在以后返回到它：  
  
```  
// rs is a CRecordset or  
// CRecordset-derived object  
  
CDBVariant varRecordToReturnTo;  
rs.GetBookmark( varRecordToReturnTo );  
  
// More code in which you  
// move to other records  
  
rs.SetBookmark( varRecordToReturnTo );  
```  
  
 不需要提取基础数据类型从[CDBVariant 类](../../mfc/reference/cdbvariant-class.md)对象。 分配的值与`GetBookmark`并返回到该书签`SetBookmark`。  
  
> [!NOTE]
>  根据你的 ODBC 驱动程序和记录集类型，可能不支持书签。 你可以轻松地确定是否通过调用支持书签[CRecordset::CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark)。 此外，如果支持书签，则必须显式选择通过指定实现它们**CRecordset::useBookmarks**选项[CRecordset::Open](../../mfc/reference/crecordset-class.md#open)成员函数。 你还应检查某些记录集操作之后的书签的持久性。 例如，如果你**Requery**记录集，书签可能不再有效。 调用[CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)若要检查是否可以安全地调用`SetBookmark`。  
  
##  <a name="_core_absolute_positions_in_mfc_odbc"></a>MFC ODBC 中的绝对位置  
 除了书签，类`CRecordset`，可通过指定序号位置来设置当前记录。 这称为绝对定位。  
  
> [!NOTE]
>  绝对定位在上不可用仅向前的记录集。 有关仅向前的记录集的详细信息，请参阅[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)。  
  
 若要移动使用绝对位置的当前记录指针，调用[CRecordset::SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition)。 当你将值传递给`SetAbsolutePosition`，对应于序号位置将成为当前记录的记录。  
  
> [!NOTE]
>  一条记录的绝对位置有可能不可靠。 如果用户从记录集，任何后续记录更改的序号位置删除记录。 书签将变为移动当前记录的推荐的方法。 有关详细信息，请参阅[MFC ODBC 中的书签](#_core_bookmarks_in_mfc_odbc)。  
  
 有关记录集导航的详细信息，请参阅[记录集： 滚动 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)