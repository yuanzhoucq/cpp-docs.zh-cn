---
title: 记录集： 滚动 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f8b5107f6e264c5d9915e809c9d198fd4cc4ba24
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053235"
---
# <a name="recordset-scrolling-odbc"></a>记录集：滚动 (ODBC)

本主题适用于 MFC ODBC 类。

打开一个记录集后，您需要访问的记录，以显示值、 执行计算，生成报告，等。 滚动记录之间移动在记录集内的允许。

本主题说明：

- [如何从一条记录滚动到另一个在记录集中](#_core_scrolling_from_one_record_to_another)。

- [在滚动的情况是，不支持](#_core_when_scrolling_is_supported)。

##  <a name="_core_scrolling_from_one_record_to_another"></a> 从一条记录滚动到另一个

类`CRecordset`提供了`Move`滚动记录集内的成员函数。 这些函数将当前记录移的行集。 如果已实现批量行提取，`Move`操作按行集的大小重新定位该记录集。 如果你尚未实现批量行提取，调用`Move`函数重新定位该记录集按逐个记录每次。 有关批量行提取的详细信息，请参阅[记录集： 提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

> [!NOTE]
>  当在记录集中移动，不能跳过已删除的记录。 有关详细信息，请参阅[IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted)成员函数。

除了`Move`函数，`CRecordset`提供用于检查是否已滚动超出末尾或开头的记录集的成员函数。

若要确定是否可以为记录集中滚动，请调用`CanScroll`成员函数。

#### <a name="to-scroll"></a>若要向下滚动

1. 将一条记录或一个行集转发： 调用[MoveNext](../../mfc/reference/crecordset-class.md#movenext)成员函数。

1. 向后的一条记录或一个行集： 调用[MovePrev](../../mfc/reference/crecordset-class.md#moveprev)成员函数。

1. 到记录集中的第一个记录： 调用[MoveFirst](../../mfc/reference/crecordset-class.md#movefirst)成员函数。

1. 到记录集中的最后一个记录或最后一个行集： 调用[MoveLast](../../mfc/reference/crecordset-class.md#movelast)成员函数。

1. *N*相对于当前的位置的记录： 调用[移动](../../mfc/reference/crecordset-class.md#move)成员函数。

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>若要测试的结尾或记录集的开头

1. 您使用滚动条滚动最后一条记录？ 调用[IsEOF](../../mfc/reference/crecordset-class.md#iseof)成员函数。

1. 是否已滚 （向后移动） 的第一个记录？ 调用[IsBOF](../../mfc/reference/crecordset-class.md#isbof)成员函数。

下面的代码示例使用`IsBOF`和`IsEOF`来检测记录集限制在任一方向滚动时显示。

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

`IsEOF` 如果记录集位于最后一条记录，则返回非零值。 `IsBOF` 如果记录集定位在第一条 （在之前的所有记录），则返回非零值。 在任一情况下，没有最新记录来操作。 如果您调用`MovePrev`时`IsBOF`已 TRUE 或调用`MoveNext`时`IsEOF`是已为 TRUE，框架将引发`CDBException`。 此外可以使用`IsBOF`和`IsEOF`检查空记录集。

有关记录集导航的详细信息，请参阅[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。

##  <a name="_core_when_scrolling_is_supported"></a> 当支持滚动

正如最初设计 SQL 提供仅向前滚动，但 ODBC 扩展了滚动功能。 对滚动的支持的可用级别取决于你的应用程序可使用您的驱动程序的 ODBC API 一致性级别，ODBC 驱动程序以及是否将 ODBC 游标库加载到内存中。 有关详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)并[ODBC: ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。

> [!TIP]
>  您可以控制是否使用游标库。 请参阅*bUseCursorLib*并*dwOptions*参数[CDatabase::Open](../../mfc/reference/cdatabase-class.md#open)。

> [!NOTE]
>  与 MFC DAO 类中，不同的 MFC ODBC 类不提供一套`Find`函数为查找满足下一步 （或上一个） 记录指定的条件。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[记录集：筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)