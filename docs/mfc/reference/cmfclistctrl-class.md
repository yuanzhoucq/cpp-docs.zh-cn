---
title: CMFCListCtrl 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 4cd1bb7787f8797984bdce5f9a5b3080d69ea5f2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62205867"
---
# <a name="cmfclistctrl-class"></a>CMFCListCtrl 类

`CMFCListCtrl`类用于扩展的功能[CListCtrl 类](../../mfc/reference/clistctrl-class.md)类通过支持的高级标头控件功能[CMFCHeaderCtrl 类](../../mfc/reference/cmfcheaderctrl-class.md)。

## <a name="syntax"></a>语法

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|可以将标记已排序的列，用不同的背景颜色的功能。|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|启用多个排序模式。|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|返回对带下划线的标头控件的引用。|
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|检查列表控件是否在多个排序模式下。|
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|它必须比较两个列表控件项时由框架调用。|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|它必须确定的单个单元格的背景色时由框架调用。|
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|它必须获取所绘制的单元格的字体时由框架调用。|
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|它必须确定的单个单元格的文本颜色时由框架调用。|
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|从已排序的列的列表中删除列排序。|
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|设置当前已排序的列和排序顺序。|
|[CMFCListCtrl::Sort](#sort)|对列表控件进行排序。|

## <a name="remarks"></a>备注

`CMFCListCtrl` 提供了两个增强功能[CListCtrl 类](../../mfc/reference/clistctrl-class.md)类。 首先，它指示列排序是可用的选项通过自动绘制排序箭头的标头。 其次，它支持在同一时间对多个列进行排序的数据。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCListCtrl` 类中的各种方法。 该示例演示如何创建列表控件、 插入列、 插入项、 设置项的文本和设置列表控件的字体。 此代码片段属于[Visual Studio 演示示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>要求

**标头：** afxlistctrl.h

##  <a name="enablemarksortedcolumn"></a>  CMFCListCtrl::EnableMarkSortedColumn

将标记已排序的列具有不同的背景色。

```
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>参数

*bMark*<br/>
[in]一个布尔型参数，用于确定是否启用不同的背景色。

*bRedraw*<br/>
[in]一个布尔型参数，用于确定是否要立即重绘控件。

### <a name="remarks"></a>备注

`EnableMarkSortedColumn` 使用方法`CDrawingManager::PixelAlpha`来计算颜色要用于排序的列。 选取颜色取决于正则背景色。

##  <a name="enablemultiplesort"></a>  CMFCListCtrl::EnableMultipleSort

启用对列表控件中的数据的行按多个列进行排序。

```
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
[in]一个布尔值，指定是否启用多个列排序模式。

### <a name="remarks"></a>备注

如果启用排序基于多个列，列具有层次结构。 首先将按主列排序的数据行。 任何等效的值再按每个后续列基于优先级。

##  <a name="getheaderctrl"></a>  CMFCListCtrl::GetHeaderCtrl

返回对标头控件的引用。

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>返回值

对基础的引用[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)对象。

### <a name="remarks"></a>备注

列表控件的标头控件是包含列标题的窗口。 它通常位于正上方的列。

##  <a name="ismultiplesort"></a>  CMFCListCtrl::IsMultipleSort

检查是否在列表控件当前支持对多个列进行排序。

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>返回值

如果列表控件支持多个排序; 则为 TRUEFALSE 否则为。

### <a name="remarks"></a>备注

当[CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)支持多个排序，用户可以按多个列进行排序列表控件中的数据。 若要启用多个排序，请调用[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)。

##  <a name="oncompareitems"></a>  CMFCListCtrl::OnCompareItems

比较两个项时，框架将调用此方法。

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>参数

*lParam1*<br/>
[in]要比较的第一个项。

*lParam2*<br/>
[in]要比较的第二个项。

*iColumn*<br/>
[in]此方法进行排序的列的索引。

### <a name="return-value"></a>返回值

一个整数，指示两个项的相对位置。 负值指示第一项应位于第二个，正值指示第一项应遵循第二个，并且零表示两个项是等效项。

### <a name="remarks"></a>备注

默认实现始终返回 0。 必须重写此函数可提供一种排序算法。

##  <a name="ongetcellbkcolor"></a>  CMFCListCtrl::OnGetCellBkColor

它必须确定的单个单元格的背景色时，框架将调用此方法。

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>参数

*nRow*<br/>
[in]相关的单元的行。

*nColumn*<br/>
[in]相关的单元的列。

### <a name="return-value"></a>返回值

一个 COLOREF 值，该值指定该单元格的背景色。

### <a name="remarks"></a>备注

默认实现`OnGetCellBkColor`不使用所提供的输入的参数，而是只需调用`GetBkColor`。 因此，默认情况下，整个列表控件将具有相同的背景色。 您可以重写`OnGetCellBkColor`用于标记具有单独的背景色的各个单元格的派生类中。

##  <a name="ongetcellfont"></a>  CMFCListCtrl::OnGetCellFont

当它获得的字体的单个单元格时，框架将调用此方法。

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>参数

*nRow*<br/>
[in]相关的单元的行。

*nColumn*<br/>
[in]相关的单元的列。

*dwData*<br/>
[in]用户定义的数据。 默认实现不使用此参数。

### <a name="return-value"></a>返回值

句柄用于当前单元格的字体。

### <a name="remarks"></a>备注

默认情况下，此方法返回 NULL。 列表控件中单元格的所有具有相同的字体。 重写此方法，以提供不同的单元格不同的字体。

##  <a name="ongetcelltextcolor"></a>  CMFCListCtrl::OnGetCellTextColor

它必须确定的单个单元格的文本颜色时，框架将调用此方法。

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>参数

*nRow*<br/>
[in]相关的单元的行。

*nColumn*<br/>
[in]相关的单元的列。

### <a name="return-value"></a>返回值

一个 COLOREF 值，该值指定该单元格的文本颜色。

### <a name="remarks"></a>备注

默认情况下，此方法调用`GetTextColor`而不考虑输入参数。 整个列表控件将具有相同的文本颜色。 您可以重写`OnGetCellTextColor`中派生的类将标记与单独的文本颜色的各个单元格。

##  <a name="removesortcolumn"></a>  CMFCListCtrl::RemoveSortColumn

从已排序的列的列表中删除列排序。

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>参数

*iColumn*<br/>
[in]要移除的列。

### <a name="remarks"></a>备注

此方法从标头控件中删除列排序。 它将调用[CMFCHeaderCtrl::RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn)。

##  <a name="setsortcolumn"></a>  CMFCListCtrl::SetSortColumn

设置当前已排序的列和排序顺序。

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>参数

*iColumn*<br/>
[in]要排序的列。

*bAscending*<br/>
[in]一个布尔值，指定的排序顺序。

*bAdd*<br/>
[in]一个布尔值，指定是否在方法中添加指示的列*iColumn*到对列进行排序的列表。

### <a name="remarks"></a>备注

此方法传递输入的参数使用方法标头控件[CMFCHeaderCtrl::SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn)。

##  <a name="sort"></a>  CMFCListCtrl::Sort

对列表控件进行排序。

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>参数

*iColumn*<br/>
[in]要排序的列。

*bAscending*<br/>
[in]一个布尔值，指定的排序顺序。

*bAdd*<br/>
[in]一个布尔值，指定此方法是否将指示的列添加*iColumn*到对列进行排序的列表。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl 类](../../mfc/reference/clistctrl-class.md)
