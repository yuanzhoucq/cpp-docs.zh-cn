---
title: 记录集：滚动 (ODBC)
ms.date: 11/04/2016
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
ms.openlocfilehash: 931051296dff495939fcbd894102a1b00e48ee90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366936"
---
# <a name="recordset-scrolling-odbc"></a>记录集：滚动 (ODBC)

本主题适用于 MFC ODBC 类。

打开记录集后，需要访问记录以显示值、执行计算、生成报告等。 通过滚动，您可以在记录集中从记录移动到记录。

本主题介绍：

- [如何在记录集中从一个记录滚动到另一个记录](#_core_scrolling_from_one_record_to_another)。

- [在什么情况下滚动是，不支持](#_core_when_scrolling_is_supported)。

## <a name="scrolling-from-one-record-to-another"></a><a name="_core_scrolling_from_one_record_to_another"></a>从一个记录滚动到另一个记录

类`CRecordset`提供`Move`用于在记录集中滚动的成员函数。 这些函数按行集移动当前记录。 如果已实现批量行提取，`Move`则操作按行集的大小重新定位记录集。 如果尚未实现批量行提取，则对`Move`函数的调用会每次都将记录集重新定位一条记录。 有关批量行提取的详细信息，请参阅[记录集：批量提取记录 （ODBC）。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

> [!NOTE]
> 在记录集中移动时，可能不会跳过已删除的记录。 有关详细信息，请参阅[IsDelete 成员](../../mfc/reference/crecordset-class.md#isdeleted)函数。

除了`Move`函数之外，`CRecordset`还提供成员函数，用于检查您是否在记录集的末尾或之前滚动过。

要确定记录集中是否可以滚动，请调用`CanScroll`成员函数。

#### <a name="to-scroll"></a>滚动

1. 转发一条记录或一个行集：调用[MoveNext](../../mfc/reference/crecordset-class.md#movenext)成员函数。

1. 向后一个记录或一个行集：调用[MovePrev](../../mfc/reference/crecordset-class.md#moveprev)成员函数。

1. 到记录集中的第一个记录：调用[MoveFirst](../../mfc/reference/crecordset-class.md#movefirst)成员函数。

1. 到记录集中或最后一个行集中的最后一个记录：调用[MoveLast](../../mfc/reference/crecordset-class.md#movelast)成员函数。

1. *N*条记录相对于当前位置：调用[移动](../../mfc/reference/crecordset-class.md#move)成员函数。

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>测试记录集的结束或开头

1. 你滚动过最后一条记录了吗？ 调用[IsEOF](../../mfc/reference/crecordset-class.md#iseof)成员函数。

1. 您是否在第一条记录之前滚动（向后移动）？ 调用[IsBOF](../../mfc/reference/crecordset-class.md#isbof)成员函数。

以下代码示例使用`IsBOF`并`IsEOF`检测记录集在任一方向滚动时的限制。

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

`IsEOF`如果记录集位于最后一条记录的过去，则返回非零值。 `IsBOF`如果记录集位于第一条记录之前（在所有记录之前），则返回非零值。 在这两种情况下，都没有要操作的当前记录。 如果在已为`MovePrev` `IsBOF` TRUE 时调用，`MoveNext`或者`IsEOF`调用时已为 TRUE，则`CDBException`框架将引发 。 您还可以使用`IsBOF`和`IsEOF`检查空记录集。

有关记录集导航的详细信息，请参阅[记录集：书签和绝对位置 （ODBC）。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

## <a name="when-scrolling-is-supported"></a><a name="_core_when_scrolling_is_supported"></a>支持滚动时

按照最初设计，SQL 仅提供前进滚动，但 ODBC 扩展滚动功能。 对滚动的可用支持级别取决于应用程序使用的 ODBC 驱动程序、驱动程序的 ODBC API 符合性级别以及 ODBC 光标库是否加载到内存中。 有关详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)和[ODBC：ODBC 光标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。

> [!TIP]
> 您可以控制是否使用游标库。 请参阅*bUseCursorLib*和*dwOptions*参数到[CDatabase：：打开](../../mfc/reference/cdatabase-class.md#open)。

> [!NOTE]
> 与 MFC DAO 类不同，MFC ODBC 类不提供`Find`一组函数来定位满足指定条件的下一个（或上一个）记录。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset：：CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[C记录集：：检查罗塞特错误](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[记录集：筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
