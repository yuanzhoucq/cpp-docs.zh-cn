---
title: 记录集：书签和绝对位置 (ODBC)
ms.date: 11/04/2016
f1_keywords:
- SetAbsolutePosition
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
ms.openlocfilehash: 77c8bbaf7c0bc21dab62c3785364e72656287815
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367070"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>记录集：书签和绝对位置 (ODBC)

本主题适用于 MFC ODBC 类。

在记录集中导航时，通常需要返回特定记录的方法。 记录的书签和绝对位置提供了两种这样的方法。

本主题介绍：

- [如何使用书签](#_core_bookmarks_in_mfc_odbc)。

- [如何使用绝对位置设置当前记录](#_core_absolute_positions_in_mfc_odbc)。

## <a name="bookmarks-in-mfc-odbc"></a><a name="_core_bookmarks_in_mfc_odbc"></a>MFC ODBC 中的书签

书签唯一标识记录。 当您浏览记录集时，不能始终依赖于记录的绝对位置，因为可以从记录集中删除记录。 跟踪记录位置的可靠方法是使用其书签。 类`CRecordset`为：

- 获取当前记录的书签，以便将其保存在变量中[（GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)）。

- 通过指定其书签快速移动到给定记录，该书签在变量[（SetBookmark）](../../mfc/reference/crecordset-class.md#setbookmark)中保存较早。

下面的示例演示如何使用这些成员函数来标记当前记录，然后返回到它：

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

不需要从[CDBVariant 类](../../mfc/reference/cdbvariant-class.md)对象中提取基础数据类型。 使用 分配值`GetBookmark`，并返回该`SetBookmark`书签。

> [!NOTE]
> 根据您的 ODBC 驱动程序和记录集类型，可能不支持书签。 通过调用[CRecordset：：canBookmark，](../../mfc/reference/crecordset-class.md#canbookmark)您可以轻松地确定书签是否受支持。 此外，如果支持书签，则必须通过在[CRecordset：：打开](../../mfc/reference/crecordset-class.md#open)成员函数中`CRecordset::useBookmarks`指定选项来显式选择实现它们。 在某些记录集操作后，还应检查书签的持久性。 例如，如果`Requery`记录集，书签可能不再有效。 调用[CDatabase：获取书签持久性](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)，以检查是否可以安全地调用`SetBookmark`。

## <a name="absolute-positions-in-mfc-odbc"></a><a name="_core_absolute_positions_in_mfc_odbc"></a>MFC ODBC 中的绝对位置

除了书签之外，类`CRecordset`还允许您通过指定一个位形位置来设置当前记录。 这称为绝对定位。

> [!NOTE]
> 绝对定位在仅转发记录集上不可用。 有关仅转发记录集的详细信息，请参阅[记录集 （ODBC）。](../../data/odbc/recordset-odbc.md)

要使用绝对位置移动当前记录指针，请调用[CRecordset：：set绝对位置](../../mfc/reference/crecordset-class.md#setabsoluteposition)。 将值传递给`SetAbsolutePosition`时，对应于该任位的记录将成为当前记录。

> [!NOTE]
> 记录的绝对位置可能不可靠。 如果用户从记录集中删除记录，则任何后续记录的任地位置将更改。 书签是移动当前记录的推荐方法。 有关详细信息，请参阅[MFC ODBC 中的书签](#_core_bookmarks_in_mfc_odbc)。

有关记录集导航的详细信息，请参阅[记录集：滚动 （ODBC）。](../../data/odbc/recordset-scrolling-odbc.md)

## <a name="see-also"></a>另请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)
