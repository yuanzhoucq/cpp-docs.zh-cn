---
title: CMFCListCtrl 类
ms.date: 07/30/2019
f1_keywords:
- CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl::EnableMarkSortedColumn
- AFXLISTCTRL/CMFCListCtrl::EnableMultipleSort
- AFXLISTCTRL/CMFCListCtrl::GetHeaderCtrl
- AFXLISTCTRL/CMFCListCtrl::IsMultipleSort
- AFXLISTCTRL/CMFCListCtrl::OnCompareItems
- AFXLISTCTRL/CMFCListCtrl::OnGetCellBkColor
- AFXLISTCTRL/CMFCListCtrl::OnGetCellFont
- AFXLISTCTRL/CMFCListCtrl::OnGetCellTextColor
- AFXLISTCTRL/CMFCListCtrl::RemoveSortColumn
- AFXLISTCTRL/CMFCListCtrl::SetSortColumn
- AFXLISTCTRL/CMFCListCtrl::Sort
helpviewer_keywords:
- CMFCListCtrl [MFC], EnableMarkSortedColumn
- CMFCListCtrl [MFC], EnableMultipleSort
- CMFCListCtrl [MFC], GetHeaderCtrl
- CMFCListCtrl [MFC], IsMultipleSort
- CMFCListCtrl [MFC], OnCompareItems
- CMFCListCtrl [MFC], OnGetCellBkColor
- CMFCListCtrl [MFC], OnGetCellFont
- CMFCListCtrl [MFC], OnGetCellTextColor
- CMFCListCtrl [MFC], RemoveSortColumn
- CMFCListCtrl [MFC], SetSortColumn
- CMFCListCtrl [MFC], Sort
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
ms.openlocfilehash: 63fbfd236ed98eee3b90f4a20b191817026903c7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370772"
---
# <a name="cmfclistctrl-class"></a>CMFCListCtrl 类

该`CMFCListCtrl`类通过支持[CMFCHeaderCtrl 类](../../mfc/reference/cmfcheaderctrl-class.md)的高级标头控制功能扩展[了 CListCtrl 类](../../mfc/reference/clistctrl-class.md)的功能。

## <a name="syntax"></a>语法

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCListctrl：：启用标记排序列](#enablemarksortedcolumn)|能够用不同的背景颜色标记已排序的列。|
|[CMFCListctrl：：启用多排序](#enablemultiplesort)|启用多个排序模式。|
|[CMFCListCtrl：：获取头Ctrl](#getheaderctrl)|返回对带下划线标头控件的引用。|
|[CMFCListctrl：：是多排序](#ismultiplesort)|检查列表控件是否处于多个排序模式。|
|[CMFCListctrl：：上比较项目](#oncompareitems)|当框架必须比较两个列表控制项时，由框架调用。|
|[CMFCListctrl：：在GetCellBkColor上](#ongetcellbkcolor)|当框架必须确定单个单元格的背景颜色时，由框架调用。|
|[CMFCListctrl：：在Getcellcellfont](#ongetcellfont)|当框架必须获取所绘制的单元格的字体时，由框架调用。|
|[CMFCListctrl：：在获取细胞文本颜色](#ongetcelltextcolor)|当框架必须确定单个单元格的文本颜色时，由框架调用。|
|[CMFCListctrl：：删除排序列](#removesortcolumn)|从排序列列表中删除排序列。|
|[CMFCListctrl：：SetSortColumn](#setsortcolumn)|设置当前排序列和排序顺序。|
|[CMFCListctrl：排序](#sort)|对列表控件进行排序。|

## <a name="remarks"></a>备注

`CMFCListCtrl`提供了[CListCtrl 类](../../mfc/reference/clistctrl-class.md)的两个增强功能。 首先，它指示列排序是一个可用选项，通过在标题上自动绘制排序箭头。 其次，它支持同时对多个列的数据排序。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCListCtrl` 类中的各种方法。 该示例演示如何创建列表控件、插入列、插入项、设置项的文本以及设置列表控件的字体。 此代码段是[可视化工作室演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>要求

**标题：** afxlistctrl.h

## <a name="cmfclistctrlenablemarksortedcolumn"></a><a name="enablemarksortedcolumn"></a>CMFCListctrl：：启用标记排序列

用不同的背景颜色标记已排序的列。

```
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>参数

*b马克*<br/>
[在]确定是否启用其他背景颜色的布尔参数。

*bredraw*<br/>
[在]确定是否立即重绘控件的布尔参数。

### <a name="remarks"></a>备注

`EnableMarkSortedColumn`使用 方法`CDrawingManager::PixelAlpha`计算对已排序列使用的颜色。 拾取的颜色基于常规背景颜色。

## <a name="cmfclistctrlenablemultiplesort"></a><a name="enablemultiplesort"></a>CMFCListctrl：：启用多排序

启用按多个列对列表控件中的数据行进行排序。

```
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]指定是否启用多个列排序模式的布尔。

### <a name="remarks"></a>备注

当您基于多个列启用排序时，列确实具有层次结构。 数据行将首先按主列排序。 然后，根据优先级按每个后续列对任何等效值进行排序。

## <a name="cmfclistctrlgetheaderctrl"></a><a name="getheaderctrl"></a>CMFCListCtrl：：获取头Ctrl

返回对标头控件的引用。

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>返回值

对基础[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)对象的引用。

### <a name="remarks"></a>备注

列表控件的标头控件是包含列标题的窗口。 它通常位于列正上方。

## <a name="cmfclistctrlismultiplesort"></a><a name="ismultiplesort"></a>CMFCListctrl：：是多排序

检查列表控件当前是否支持对多个列进行排序。

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>返回值

如果列表控件支持多个排序，则为 TRUE;如果列表控件支持多个排序。"否则。

### <a name="remarks"></a>备注

当[CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)支持多个排序时，用户可以按多个列对列表控件中的数据进行排序。 要启用多个排序，请致电[CMFCListCtrl：：启用多排序](#enablemultiplesort)。

## <a name="cmfclistctrloncompareitems"></a><a name="oncompareitems"></a>CMFCListctrl：：上比较项目

框架在比较两个项目时调用此方法。

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>参数

*lParam1*<br/>
[在]要比较的第一项。

*lParam2*<br/>
[在]要比较的第二个项目。

*iColumn*<br/>
[在]此方法正在排序的列的索引。

### <a name="return-value"></a>返回值

指示两个项的相对位置的整数。 负值表示第一个项应位于第二个项之前，正值表示第一个项应遵循第二个项，零表示两个项等效。

### <a name="remarks"></a>备注

默认实现始终返回 0。 重写此函数以提供您自己的排序算法。

## <a name="cmfclistctrlongetcellbkcolor"></a><a name="ongetcellbkcolor"></a>CMFCListctrl：：在GetCellBkColor上

当框架必须确定单个单元格的背景颜色时，该框架将调用此方法。

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>参数

*nRow*<br/>
[在]有问题的单元格的行。

*nColumn*<br/>
[在]有问题的单元格的列。

### <a name="return-value"></a>返回值

指定单元格背景颜色的 COLOREF 值。

### <a name="remarks"></a>备注

的`OnGetCellBkColor`默认实现不使用提供的输入参数，而只是调用`GetBkColor`。 因此，默认情况下，整个列表控件将具有相同的背景颜色。 可以在派生类`OnGetCellBkColor`中重写以标记具有单独背景颜色的各个单元格。

## <a name="cmfclistctrlongetcellfont"></a><a name="ongetcellfont"></a>CMFCListctrl：：在Getcellcellfont

当框架获取单个单元格的字体时，它将调用此方法。

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>参数

*nRow*<br/>
[在]有问题的单元格的行。

*nColumn*<br/>
[在]有问题的单元格的列。

*dwData*<br/>
[在]用户定义的数据。 默认实现不使用此参数。

### <a name="return-value"></a>返回值

用于当前单元格的字体的句柄。

### <a name="remarks"></a>备注

默认情况下，此方法返回 NULL。 列表控件中的所有单元格具有相同的字体。 重写此方法，为不同的单元格提供不同的字体。

## <a name="cmfclistctrlongetcelltextcolor"></a><a name="ongetcelltextcolor"></a>CMFCListctrl：：在获取细胞文本颜色

当框架必须确定单个单元格的文本颜色时，它将调用此方法。

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>参数

*nRow*<br/>
[在]有问题的单元格的行。

*nColumn*<br/>
[在]有问题的单元格的列。

### <a name="return-value"></a>返回值

指定单元格的文本颜色的 COLOREF 值。

### <a name="remarks"></a>备注

默认情况下，此方法调用`GetTextColor`，而不考虑输入参数。 整个列表控件将具有相同的文本颜色。 可以在派生类`OnGetCellTextColor`中重写以标记具有单独文本颜色的各个单元格。

## <a name="cmfclistctrlremovesortcolumn"></a><a name="removesortcolumn"></a>CMFCListctrl：：删除排序列

从排序列列表中删除排序列。

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>参数

*iColumn*<br/>
[在]要删除的列。

### <a name="remarks"></a>备注

此方法从标头控件中删除排序列。 它调用[CMFCHeaderCtrl：：删除排序列](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn)。

## <a name="cmfclistctrlsetsortcolumn"></a><a name="setsortcolumn"></a>CMFCListctrl：：SetSortColumn

设置当前排序列和排序顺序。

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>参数

*iColumn*<br/>
[在]要排序的列。

*b 上升*<br/>
[在]指定排序顺序的布尔。

*bAdd*<br/>
[在]指定方法是否将*iColumn*指示的列添加到排序列列表中的布尔。

### <a name="remarks"></a>备注

此方法使用[CMFCHeaderCtrl：：setSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn)的方法将输入参数传递给标头控件。

## <a name="cmfclistctrlsort"></a><a name="sort"></a>CMFCListctrl：排序

对列表控件进行排序。

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>参数

*iColumn*<br/>
[在]要排序的列。

*b 上升*<br/>
[在]指定排序顺序的布尔。

*bAdd*<br/>
[在]指定此方法是否将*iColumn*指示的列添加到排序列列表中的布尔。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl 类](../../mfc/reference/clistctrl-class.md)
