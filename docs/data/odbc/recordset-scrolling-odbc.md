---
title: 记录集： 滚动 (ODBC) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- recordsets [C++], end of
- recordsets [C++], beginning of
- navigation [C++], recordsets
- recordsets [C++], moving to records
- ODBC recordsets, scrolling
- recordsets [C++], navigating
- scrolling [C++], recordsets
- Move method (recordsets)
ms.assetid: f38d2dcb-1e88-4e41-af25-98b00c276be4
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 34dcfb9cb1d45710accba2ee6155e3c741b727be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-scrolling-odbc"></a>记录集：滚动 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 打开记录集后，你需要访问的记录，以显示值、 进行计算、 生成报告，依次类推。 滚动记录之间移动在记录集中的允许。  
  
 本主题说明：  
  
-   [如何从一个记录滚动到另一个在记录集中](#_core_scrolling_from_one_record_to_another)。  
  
-   [在滚动的情况下是和不支持下](#_core_when_scrolling_is_supported)。  
  
##  <a name="_core_scrolling_from_one_record_to_another"></a>从一个记录滚动到另一个  
 类`CRecordset`提供**移动**滚动在记录集中的成员函数。 这些函数按行集移动当前记录。 如果已实现批量行提取，**移动**操作按行集的大小重新定位记录集。 如果你尚未在实现批量行提取，调用**移动**函数记录集按记录重新定位一个每次。 有关批量行提取的详细信息，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
> [!NOTE]
>  当在记录集中移动，不能跳过已删除的记录。 有关详细信息，请参阅[IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted)成员函数。  
  
 除了**移动**函数，`CRecordset`提供成员函数检查是否有滚动末尾或记录集中的开头。  
  
 若要确定是否记录集中可以滚动，调用`CanScroll`成员函数。  
  
#### <a name="to-scroll"></a>若要向下滚动  
  
1.  将一个记录或一个行集转发： 调用[MoveNext](../../mfc/reference/crecordset-class.md#movenext)成员函数。  
  
2.  向后的一条记录或一个行集： 调用[MovePrev](../../mfc/reference/crecordset-class.md#moveprev)成员函数。  
  
3.  在记录集中的第一个记录： 调用[MoveFirst](../../mfc/reference/crecordset-class.md#movefirst)成员函数。  
  
4.  在记录集中的最新记录到或最后一个行集： 调用[MoveLast](../../mfc/reference/crecordset-class.md#movelast)成员函数。  
  
5.  *N*相对于当前的位置的记录： 调用[移动](../../mfc/reference/crecordset-class.md#move)成员函数。  
  
#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>若要测试的结尾或记录集的开头  
  
1.  你具有滚动最后一条记录？ 调用[IsEOF](../../mfc/reference/crecordset-class.md#iseof)成员函数。  
  
2.  是否已滚 （向后移动） 的第一个记录？ 调用[IsBOF](../../mfc/reference/crecordset-class.md#isbof)成员函数。  
  
 下面的代码示例使用`IsBOF`和`IsEOF`来检测何时在任一方向滚动的记录集的限制。  
  
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
  
 `IsEOF`如果记录集定位最后一条记录，则返回非零值。 `IsBOF`如果记录集定位之前 （在之前的所有记录） 的第一个记录，则返回非零值。 在任一情况下，没有最新的记录上进行操作。 如果调用`MovePrev`时`IsBOF`已**TRUE**或调用`MoveNext`时`IsEOF`已**TRUE**，框架将引发`CDBException`。 你还可以使用`IsBOF`和`IsEOF`检查空的记录集。  
  
 有关记录集导航的详细信息，请参阅[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。  
  
##  <a name="_core_when_scrolling_is_supported"></a>支持滚动时  
 正如最初设计，SQL 提供仅向前滚动，但 ODBC 扩展了滚动功能。 可用的滚动的支持级别取决于使用驱动程序的 ODBC API 一致性级别，你的应用程序的 ODBC 驱动程序和 ODBC 游标库是否已加载到内存。 有关详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)和[ODBC: ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
> [!TIP]
>  你可以控制是否使用的是光标库。 请参阅`bUseCursorLib`和`dwOptions`参数[CDatabase::Open](../../mfc/reference/cdatabase-class.md#open)。  
  
> [!NOTE]
>  与 MFC DAO 类中，不同的 MFC ODBC 类不提供一套**查找**函数为查找满足下一步 （或先前） 记录指定的条件。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)   
 [CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)   
 [记录集：筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)