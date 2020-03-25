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
ms.openlocfilehash: 8a8305d2acacc79f5d7fe395087a0bd13dcbd196
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212766"
---
# <a name="recordset-scrolling-odbc"></a>记录集：滚动 (ODBC)

本主题适用于 MFC ODBC 类。

打开记录集之后，您需要访问这些记录以显示值、进行计算、生成报表等。 滚动使你可以在记录集中从记录移动到记录。

本主题介绍：

- [如何在记录集中从一个记录滚动到另一个记录](#_core_scrolling_from_one_record_to_another)。

- [在什么情况下，滚动是不受支持](#_core_when_scrolling_is_supported)的。

##  <a name="scrolling-from-one-record-to-another"></a><a name="_core_scrolling_from_one_record_to_another"></a>从一个记录滚动到另一个记录

类 `CRecordset` 提供 `Move` 成员函数以便在记录集中滚动。 这些函数按行集移动当前记录。 如果已实现批量行提取，`Move` 操作会按行集的大小重新定位记录集。 如果尚未实现批量行提取，则调用 `Move` 函数每次都会重新定位记录集。 有关批量行提取的详细信息，请参阅[记录集：批量提取记录（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

> [!NOTE]
>  在记录集中时，可能不会跳过已删除的记录。 有关详细信息，请参阅[IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted)成员函数。

除了 `Move` 函数外，`CRecordset` 还提供了成员函数，用于检查您是滚动到记录集开头之前还是之后。

若要确定是否可以在记录集中进行滚动，请调用 `CanScroll` 成员函数。

#### <a name="to-scroll"></a>滚动

1. 转发一个记录或一个行集：调用[MoveNext](../../mfc/reference/crecordset-class.md#movenext)成员函数。

1. 向后一条记录或一个行集：调用[MovePrev](../../mfc/reference/crecordset-class.md#moveprev)成员函数。

1. 记录到记录集中的第一条记录：调用[MoveFirst](../../mfc/reference/crecordset-class.md#movefirst)成员函数。

1. 到记录集中的最后一条记录或最后一个行集：调用[MoveLast](../../mfc/reference/crecordset-class.md#movelast)成员函数。

1. 相对于当前位置的*N*条记录：调用[移动](../../mfc/reference/crecordset-class.md#move)成员函数。

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>测试记录集的结尾还是开头

1. 是否已滚动到最后一条记录？ 调用[IsEOF](../../mfc/reference/crecordset-class.md#iseof)成员函数。

1. 是否向前滚动第一条记录（向后移动）？ 调用[IsBOF](../../mfc/reference/crecordset-class.md#isbof)成员函数。

下面的代码示例使用 `IsBOF` 和 `IsEOF` 来检测在任一方向滚动时记录集的限制。

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

如果记录集位于最后一条记录之后，`IsEOF` 将返回一个非零值。 如果记录集位于第一条记录（在所有记录之前）之前，`IsBOF` 将返回一个非零值。 在任一情况下，都没有要操作的当前记录。 如果在 `IsBOF` 已为 TRUE 时调用 `MovePrev`，或在 `IsEOF` 已为 TRUE 时调用 `MoveNext`，则该框架将引发 `CDBException`。 你还可以使用 `IsBOF` 和 `IsEOF` 检查是否有空记录集。

有关记录集导航的详细信息，请参阅[记录集：书签和绝对位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。

##  <a name="when-scrolling-is-supported"></a><a name="_core_when_scrolling_is_supported"></a>支持滚动时

如前所述，SQL 仅提供向前滚动功能，但 ODBC 扩展了滚动功能。 对滚动的可用支持级别取决于应用程序所使用的 ODBC 驱动程序、驱动程序的 ODBC API 一致性级别，以及 ODBC 游标库是否已加载到内存中。 有关详细信息，请参阅[odbc](../../data/odbc/odbc-basics.md)和[Odbc： odbc 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。

> [!TIP]
>  您可以控制是否使用游标库。 请参阅*bUseCursorLib*和*DwOptions*参数到[CDatabase：： Open](../../mfc/reference/cdatabase-class.md#open)。

> [!NOTE]
>  与 MFC DAO 类不同，MFC ODBC 类不提供一组用于查找满足指定条件的下一个（或上一个）记录的 `Find` 函数。

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset：： CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset：： CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[记录集：筛选记录 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
