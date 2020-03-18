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
ms.openlocfilehash: 599a00af28ee5b8effbabbe5b334022ceb49f91a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425819"
---
# <a name="cmfclistctrl-class"></a>CMFCListCtrl 类

`CMFCListCtrl` 类通过支持[CMFCHeaderCtrl 类](../../mfc/reference/cmfcheaderctrl-class.md)的高级标头控件功能，扩展了[CListCtrl 类](../../mfc/reference/clistctrl-class.md)的功能。

## <a name="syntax"></a>语法

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|允许用不同背景色标记已排序的列。|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|启用多个排序模式。|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|返回对带下划线的标头控件的引用。|
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|检查列表控件是否处于多个排序模式。|
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|当必须比较两个列表控件项时，由框架调用。|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|当必须确定单个单元格的背景色时，由框架调用。|
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|当必须获取正在绘制的单元格的字体时，由框架调用。|
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|当必须确定单个单元格的文本颜色时，由框架调用。|
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|从已排序的列的列表中删除排序列。|
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|设置当前已排序的列和排序顺序。|
|[CMFCListCtrl：： Sort](#sort)|对列表控件进行排序。|

## <a name="remarks"></a>备注

`CMFCListCtrl` 提供[CListCtrl 类](../../mfc/reference/clistctrl-class.md)的两个增强功能。 首先，它指示列排序是可用选项，方法是在标头上自动绘制排序箭头。 其次，它支持同时对多个列进行数据排序。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCListCtrl` 类中的各种方法。 该示例演示如何创建列表控件、插入列、插入项、设置项的文本以及设置列表控件的字体。 此代码片段是[Visual Studio 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>要求

**标头：** afxlistctrl

##  <a name="enablemarksortedcolumn"></a>CMFCListCtrl::EnableMarkSortedColumn

用不同的背景色标记已排序的列。

```
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>parameters

*bMark*<br/>
中确定是否启用不同背景色的布尔型参数。

*bRedraw*<br/>
中一个布尔参数，确定是否立即重绘控件。

### <a name="remarks"></a>备注

`EnableMarkSortedColumn` 使用方法 `CDrawingManager::PixelAlpha` 来计算要用于已排序的列的颜色。 选取的颜色基于常规背景色。

##  <a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort

允许按多个列对列表控件中的数据行进行排序。

```
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>parameters

*bEnable*<br/>
中一个布尔值，指定是否要启用多个列排序模式。

### <a name="remarks"></a>备注

如果启用基于多列的排序，则这些列具有层次结构。 数据行将首先按主列排序。 然后，将根据优先级按每个后续列对任何等效值进行排序。

##  <a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl

返回对标头控件的引用。

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>返回值

对基础[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)对象的引用。

### <a name="remarks"></a>备注

列表控件的标头控件是包含列标题的窗口。 它通常位于列的正上方。

##  <a name="ismultiplesort"></a>CMFCListCtrl::IsMultipleSort

检查列表控件当前是否支持对多个列进行排序。

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>返回值

如果列表控件支持多个排序，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

当[CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)支持多个排序时，用户可以按多个列对列表控件中的数据进行排序。 若要启用多个排序，请调用[CMFCListCtrl：： EnableMultipleSort](#enablemultiplesort)。

##  <a name="oncompareitems"></a>CMFCListCtrl::OnCompareItems

框架在比较两个项时调用此方法。

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>parameters

*lParam1*<br/>
中要比较的第一项。

*lParam2*<br/>
中要比较的第二项。

*iColumn*<br/>
中此方法正在排序的列的索引。

### <a name="return-value"></a>返回值

一个整数，指示两个项的相对位置。 负值指示第一项应在第二个项之前，正值指示第一项应在第二项之后，0表示两项等效。

### <a name="remarks"></a>备注

默认实现始终返回0。 重写此函数以提供您自己的排序算法。

##  <a name="ongetcellbkcolor"></a>CMFCListCtrl::OnGetCellBkColor

当框架必须确定单个单元格的背景色时，框架会调用此方法。

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>parameters

*nRow*<br/>
中相关单元格的行。

*nColumn*<br/>
中相关单元格的列。

### <a name="return-value"></a>返回值

一个 COLOREF 值，该值指定单元格的背景色。

### <a name="remarks"></a>备注

`OnGetCellBkColor` 的默认实现不使用提供的输入参数，而只是调用 `GetBkColor`。 因此，默认情况下，整个列表控件将具有相同的背景色。 您可以在派生类中重写 `OnGetCellBkColor`，以使用单独的背景色标记各个单元。

##  <a name="ongetcellfont"></a>CMFCListCtrl::OnGetCellFont

框架在获取单个单元格的字体时将调用此方法。

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>parameters

*nRow*<br/>
中相关单元格的行。

*nColumn*<br/>
中相关单元格的列。

*dwData*<br/>
中用户定义数据。 默认实现不使用此参数。

### <a name="return-value"></a>返回值

用于当前单元格的字体的句柄。

### <a name="remarks"></a>备注

默认情况下，此方法返回 NULL。 列表控件中的所有单元格都具有相同的字体。 重写此方法可为不同的单元格提供不同的字体。

##  <a name="ongetcelltextcolor"></a>CMFCListCtrl::OnGetCellTextColor

当框架必须确定单个单元格的文本颜色时，框架会调用此方法。

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>parameters

*nRow*<br/>
中相关单元格的行。

*nColumn*<br/>
中相关单元格的列。

### <a name="return-value"></a>返回值

一个 COLOREF 值，该值指定单元格的文本颜色。

### <a name="remarks"></a>备注

默认情况下，此方法将调用 `GetTextColor`，而不考虑输入参数。 整个 list 控件将具有相同的文本颜色。 可以在派生类中重写 `OnGetCellTextColor`，以使用单独的文本颜色标记单独的单元格。

##  <a name="removesortcolumn"></a>CMFCListCtrl::RemoveSortColumn

从已排序的列的列表中删除排序列。

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>parameters

*iColumn*<br/>
中要删除的列。

### <a name="remarks"></a>备注

此方法从标题控件中删除排序列。 它调用[CMFCHeaderCtrl：： RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn)。

##  <a name="setsortcolumn"></a>CMFCListCtrl::SetSortColumn

设置当前已排序的列和排序顺序。

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>parameters

*iColumn*<br/>
中要排序的列。

*bAscending*<br/>
中指定排序顺序的布尔值。

*b*<br/>
中一个布尔值，指定方法是否将*iColumn*指示的列添加到排序列列表。

### <a name="remarks"></a>备注

此方法通过使用方法[CMFCHeaderCtrl：： SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn)将输入参数传递给标头控件。

##  <a name="sort"></a>CMFCListCtrl：： Sort

对列表控件进行排序。

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>parameters

*iColumn*<br/>
中要排序的列。

*bAscending*<br/>
中指定排序顺序的布尔值。

*b*<br/>
中指定此方法是否将*iColumn*指示的列添加到排序列列表中的布尔值。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl 类](../../mfc/reference/clistctrl-class.md)
