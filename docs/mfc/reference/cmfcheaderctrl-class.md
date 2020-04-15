---
title: CListCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::EnableMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::GetColumnState
- AFXHEADERCTRL/CMFCHeaderCtrl::GetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::IsAscending
- AFXHEADERCTRL/CMFCHeaderCtrl::IsDialogControl
- AFXHEADERCTRL/CMFCHeaderCtrl::IsMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::RemoveSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::SetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawItem
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawSortArrow
- AFXHEADERCTRL/CMFCHeaderCtrl::OnFillBackground
helpviewer_keywords:
- CMFCHeaderCtrl [MFC], CMFCHeaderCtrl
- CMFCHeaderCtrl [MFC], EnableMultipleSort
- CMFCHeaderCtrl [MFC], GetColumnState
- CMFCHeaderCtrl [MFC], GetSortColumn
- CMFCHeaderCtrl [MFC], IsAscending
- CMFCHeaderCtrl [MFC], IsDialogControl
- CMFCHeaderCtrl [MFC], IsMultipleSort
- CMFCHeaderCtrl [MFC], RemoveSortColumn
- CMFCHeaderCtrl [MFC], SetSortColumn
- CMFCHeaderCtrl [MFC], OnDrawItem
- CMFCHeaderCtrl [MFC], OnDrawSortArrow
- CMFCHeaderCtrl [MFC], OnFillBackground
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
ms.openlocfilehash: 0a6b0cf39861ba995acff71fc40cf44ae5114642
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367450"
---
# <a name="cmfcheaderctrl-class"></a>CListCtrl

类`CMFCHeaderCtrl`支持对标头控件中的多列进行排序。

## <a name="syntax"></a>语法

```
class CMFCHeaderCtrl : public CHeaderCtrl
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFCHeaderCtrl：：CMFCHeaderCtrl](#cmfcheaderctrl)|构造 `CMFCHeaderCtrl` 对象。|
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCHeaderctrl：：启用多排序](#enablemultiplesort)|为当前标头控件启用或禁用*多个列排序*模式。|
|[CMFCHeaderctrl：：获取列格状态](#getcolumnstate)|指示列是未排序，还是按升序或降序排序。|
|[CMFCHeaderctrl：：获取排序柱](#getsortcolumn)|检索标头控件中第一个排序列的零基索引。|
|`CMFCHeaderCtrl::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCHeaderCtrl：正在提升](#isascending)|指示标题控件中的任何列是否按升序排序。|
|[CMFCheaderctrl：：IsDialog控制](#isdialogcontrol)|指示当前标头控件的父窗口是否是对话框。|
|[CMFCHeaderctrl：：是多排序](#ismultiplesort)|指示当前标头控件是否处于*多个列排序*模式。|
|[CMFCHeaderctrl：：删除排序列](#removesortcolumn)|从排序列列表中删除指定的列。|
|[CMFCHeaderctrl：：SetSortColumn](#setsortcolumn)|设置标题控件中指定列的排序顺序。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFCheaderctrl：：在绘制项目](#ondrawitem)|由框架调用以绘制标题控件列。|
|[CMFCheaderctrl：：OndrawSortArrow](#ondrawsortarrow)|由框架调用以绘制排序箭头。|
|[CMFCheaderctrl：：在填充背景](#onfillbackground)|由框架调用以填充标头控制列的背景。|

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCHeaderCtrl`类的对象，以及如何为当前标头控件启用*多个列排序*模式。

[!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]

## <a name="remarks"></a>备注

类`CMFCHeaderCtrl`在标题控件列上绘制排序箭头以指示该列已排序。 如果父列表控件 （ [CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)） 中的一组列可以同时排序，请使用*多个列排序*模式。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)

[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)

## <a name="requirements"></a>要求

**标题：** afxheaderctrl.h

## <a name="cmfcheaderctrlcmfcheaderctrl"></a><a name="cmfcheaderctrl"></a>CMFCHeaderCtrl：：CMFCHeaderCtrl

构造 `CMFCHeaderCtrl` 对象。

```
CMFCHeaderCtrl::CMFCHeaderCtrl()
```

### <a name="remarks"></a>备注

此构造函数将以下成员变量初始化到指定值：

|成员变量|“值”|
|---------------------|-----------|
|`m_bIsMousePressed`|FALSE|
|`m_bMultipleSort`|FALSE|
|`m_bAscending`|TRUE|
|`m_nHighlightedItem`|-1|
|`m_bTracked`|FALSE|
|`m_bIsDlgControl`|FALSE|
|`m_hFont`|Null|

## <a name="cmfcheaderctrlenablemultiplesort"></a><a name="enablemultiplesort"></a>CMFCHeaderctrl：：启用多排序

为当前标头控件启用或禁用*多个列排序*模式。

```
void EnableMultipleSort(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]TRUE 启用多列排序模式;FALSE 禁用多个列排序模式，并从已排序列列表中删除任何列。 默认值为 TRUE。

### <a name="remarks"></a>备注

使用此方法可启用或禁用多个列排序模式。 如果标题控件处于多个列排序模式，则两个或多个列可以参与排序。

## <a name="cmfcheaderctrlgetcolumnstate"></a><a name="getcolumnstate"></a>CMFCHeaderctrl：：获取列格状态

指示列是未排序，还是按升序或降序排序。

```
int GetColumnState(int iColumn) const;
```

### <a name="parameters"></a>参数

*iColumn*<br/>
[在]列的零基索引。

### <a name="return-value"></a>返回值

指示指定列的排序状态的值。 下表列出了可能的值：

|“值”|描述|
|-----------|-----------------|
|-1|按降序排序。|
|0|未排序。|
|1|按升序排序。|

### <a name="remarks"></a>备注

## <a name="cmfcheaderctrlgetsortcolumn"></a><a name="getsortcolumn"></a>CMFCHeaderctrl：：获取排序柱

检索标头控件中第一个排序列的零基索引。

```
int GetSortColumn() const;
```

### <a name="return-value"></a>返回值

未找到已排序列的索引，或 -1。如果未找到已排序列。

### <a name="remarks"></a>备注

如果标头控件处于*多个列排序*模式，并且您在调试模式下编译应用程序，则此方法断言并建议您改用[CMFCHeaderCtrl：：getColumnState](#getcolumnstate)方法。 如果标头控件处于多个列排序模式，并且您在零售模式下编译应用程序，则此方法返回 -1。

## <a name="cmfcheaderctrlisascending"></a><a name="isascending"></a>CMFCHeaderCtrl：正在提升

指示标题控件中的任何列是否按升序排序。

```
BOOL IsAscending() const;
```

### <a name="return-value"></a>返回值

如果标题控件中的任何列按升序排序，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法返回的值用于在标头控制项上显示适当的排序箭头。 使用[CMFCHeaderCtrl：：SetSortColumn](#setsortcolumn)方法设置排序顺序。

## <a name="cmfcheaderctrlisdialogcontrol"></a><a name="isdialogcontrol"></a>CMFCheaderctrl：：IsDialog控制

指示当前标头控件的父窗口是否是对话框。

```
BOOL IsDialogControl() const;
```

### <a name="return-value"></a>返回值

如果当前标头控件的父窗口是对话框，则为 TRUE;否则，FALSE。

## <a name="cmfcheaderctrlismultiplesort"></a><a name="ismultiplesort"></a>CMFCHeaderctrl：：是多排序

指示当前标头控件是否处于*多个列排序*模式。

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>返回值

如果启用了多个列排序模式，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

使用[CMFCHeaderCtrl：启用多排序](#enablemultiplesort)方法以启用或禁用多个列排序模式。 如果标题控件处于多个列排序模式，则两个或多个列可以参与排序。

## <a name="cmfcheaderctrlondrawitem"></a><a name="ondrawitem"></a>CMFCheaderctrl：：在绘制项目

由框架调用以绘制标题控件列。

```
virtual void OnDrawItem(
    CDC* pDC,
    int iItem,
    CRect rect,
    BOOL bIsPressed,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*iItem*<br/>
[在]要绘制的项的零基索引。

*矩形*<br/>
[在]要绘制的项的边界矩形。

*bIsPressed*<br/>
[在]TRUE 以按压状态绘制项目;否则，FALSE。

*bIs 突出显示*<br/>
[在]TRUE 以突出显示状态绘制项目;如果为 TRUE，则为"TRUE"，以"TRUE"状态绘制项目。否则，FALSE。

## <a name="cmfcheaderctrlondrawsortarrow"></a><a name="ondrawsortarrow"></a>CMFCheaderctrl：：OndrawSortArrow

由框架调用以绘制排序箭头。

```
virtual void OnDrawSortArrow(
    CDC* pDC,
    CRect rectArrow);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*雷克拉罗*<br/>
[在]排序箭头的边界矩形。

## <a name="cmfcheaderctrlonfillbackground"></a><a name="onfillbackground"></a>CMFCheaderctrl：：在填充背景

由框架调用以填充标头控制列的背景。

```
virtual void OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

### <a name="remarks"></a>备注

## <a name="cmfcheaderctrlremovesortcolumn"></a><a name="removesortcolumn"></a>CMFCHeaderctrl：：删除排序列

从排序列列表中删除指定的列。

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>参数

*iColumn*<br/>
[在]要删除的列的零基索引。

## <a name="cmfcheaderctrlsetsortcolumn"></a><a name="setsortcolumn"></a>CMFCHeaderctrl：：SetSortColumn

设置标题控件中指定列的排序顺序。

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending=TRUE,
    BOOL bAdd=FALSE);
```

### <a name="parameters"></a>参数

*iColumn*<br/>
[在]标头控件列的零基索引。 如果此参数小于零，此方法将从排序列列表中删除所有列。

*b 上升*<br/>
[在]指定*iColumn*参数指定的列的排序顺序。 真实设置提升顺序;FALSE 以设置降序。 默认值为 TRUE。

*bAdd*<br/>
[在]TRUE 设置为*iColumn*参数指定的列的排序顺序。

如果当前标头控件处于*多个列排序*模式，则此方法将指定的列添加到排序列列表中。 使用[CMFCHeaderCtrl：启用多排序](#enablemultiplesort)以设置多个列排序模式。

如果未设置多个列排序模式，并且此方法在调试模式下编译，则此方法断言。 如果未设置多个列排序模式，并且此方法在零售模式下编译，则此方法首先从排序列列表中删除所有列，然后将指定的列添加到列表中。

FALSE 首先从排序列列表中删除所有列，然后将指定的列添加到列表中。 默认值是 FALSE。

### <a name="remarks"></a>备注

使用此方法设置列的排序顺序。 如有必要，此方法将列添加到排序列列表中。 标题控件使用排序顺序绘制向上或向下点的排序箭头。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)
